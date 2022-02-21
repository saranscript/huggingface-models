---
language: rw
datasets:
- common_voice
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Large Kinyarwanda no punctuation
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice rw
      type: common_voice
      args: rw
    metrics:
       - name: Test WER
         type: wer
         value: 40.59
---

# Wav2Vec2-Large-XLSR-53-rw

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Kinyarwanda using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset, using about 20% of the training data (limited to utterances without downvotes and shorter than 9.5 seconds), and validated on 2048 utterances from the validation set. In contrast to the [lucio/wav2vec2-large-xlsr-kinyarwanda-apostrophied](https://huggingface.co/lucio/wav2vec2-large-xlsr-kinyarwanda-apostrophied) model, which predicts the apostrophes that mark contractions of pronouns with vowel-initial words, this model does not predict any punctuation.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

# WARNING! This will download and extract to use about 80GB on disk.
test_dataset = load_dataset("common_voice", "rw", split="test[:2%]") 

processor = Wav2Vec2Processor.from_pretrained("lucio/wav2vec2-large-xlsr-kinyarwanda") 
model = Wav2Vec2ForCTC.from_pretrained("lucio/wav2vec2-large-xlsr-kinyarwanda")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset[:2]["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```

Result:
```
Prediction: ['yaherukaga gukora igitaramo y iki mu jyiwa na mul mumbiliki', 'ini rero ntibizashoboka ka nibo nkunrabibzi']
Reference: ['Yaherukaga gukora igitaramo nk’iki mu Mujyi wa Namur mu Bubiligi.', 'Ibi rero, ntibizashoboka, kandi nawe arabizi.']
```

## Evaluation

The model can be evaluated as follows on the Kinyarwanda test data of Common Voice. Note that to even load the test data, the whole 40GB Kinyarwanda dataset will be downloaded and extracted into another 40GB directory, so you will need that space available on disk (e.g. not possible in the free tier of Google Colab). This script uses the `chunked_wer` function from [pcuenq](https://huggingface.co/pcuenq/wav2vec2-large-xlsr-53-es).


```python
import jiwer
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
import unidecode

test_dataset = load_dataset("common_voice", "rw", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("lucio/wav2vec2-large-xlsr-kinyarwanda") 
model = Wav2Vec2ForCTC.from_pretrained("lucio/wav2vec2-large-xlsr-kinyarwanda")
model.to("cuda")

chars_to_ignore_regex = r'[!"#$%&()*+,./:;<=>?@\[\]\\_{}|~£¤¨©ª«¬®¯°·¸»¼½¾ðʺ˜˝ˮ‐–—―‚“”„‟•…″‽₋€™−√�]'

def remove_special_characters(batch):
    batch["text"] = re.sub(r'[ʻʽʼ‘’´`]', r"'", batch["sentence"])  # normalize apostrophes
    batch["text"] = re.sub(chars_to_ignore_regex, "", batch["text"]).lower().strip()  # remove all other punctuation
    batch["text"] = re.sub(r"(-| ?' ?|  +)", " ", batch["text"])  # treat dash and apostrophe as word boundary
    batch["text"] = unidecode.unidecode(batch["text"])  # strip accents
    return batch

## Audio pre-processing
resampler = torchaudio.transforms.Resample(48_000, 16_000)

def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    batch["sampling_rate"] = 16_000
    return batch

def cv_prepare(batch):
    batch = remove_special_characters(batch)
    batch = speech_file_to_array_fn(batch)
    return batch
    
test_dataset = test_dataset.map(cv_prepare)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

def chunked_wer(targets, predictions, chunk_size=None):                                          
    if chunk_size is None: return jiwer.wer(targets, predictions)                                
    start = 0                                                                                    
    end = chunk_size                                                                             
    H, S, D, I = 0, 0, 0, 0                                                                      
    while start < len(targets):                                                                  
        chunk_metrics = jiwer.compute_measures(targets[start:end], predictions[start:end])       
        H = H + chunk_metrics["hits"]                                                            
        S = S + chunk_metrics["substitutions"]                                                   
        D = D + chunk_metrics["deletions"]                                                       
        I = I + chunk_metrics["insertions"]                                                      
        start += chunk_size                                                                      
        end += chunk_size                                                                        
    return float(S + D + I) / float(H + S + D)

print("WER: {:2f}".format(100 * chunked_wer(result["sentence"], result["pred_strings"], chunk_size=4000)))
```

**Test Result**: 40.59 % 


## Training

Blocks of examples from the Common Voice training dataset were used for training, after filtering out utterances that had any `down_vote` or were longer than 9.5 seconds. The data used totals about 100k examples, 20% of the available data. Training proceeded for 30k global steps, on 1 V100 GPU provided by OVHcloud. For validation, 2048 examples of the validation dataset were used.

The [script used for training](https://github.com/serapio/transformers/blob/feature/xlsr-finetune/examples/research_projects/wav2vec2/run_common_voice.py) is adapted from the [example script provided in the transformers repo](https://github.com/huggingface/transformers/blob/master/examples/research_projects/wav2vec2/run_common_voice.py).