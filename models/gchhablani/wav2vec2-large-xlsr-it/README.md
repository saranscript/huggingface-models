---
language: it
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
- name: Wav2Vec2 Large 53 Italian by Gunjan Chhablani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice it
      type: common_voice
      args: it
    metrics:
       - name: Test WER
         type: wer
         value: 11.49
---

# Wav2Vec2-Large-XLSR-53-Italian
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Italian using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset. 
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "it", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained('gchhablani/wav2vec2-large-xlsr-it')
model = Wav2Vec2ForCTC.from_pretrained('gchhablani/wav2vec2-large-xlsr-it') 

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["sentence"][:2])
```


## Evaluation

The model can be evaluated as follows on the Portuguese test data of Common Voice.


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

import unicodedata
import jiwer

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

allowed_characters = [
    " ",
    "'",
    'a',
    'b',
    'c',
    'd',
    'e',
    'f',
    'g',
    'h',
    'i',
    'j',
    'k',
    'l',
    'm',
    'n',
    'o',
    'p',
    'q',
    'r',
    's',
    't',
    'u',
    'v',
    'w',
    'x',
    'y',
    'z',
    'à',
    'á',
    'è',
    'é',
    'ì',
    'í',
    'ò',
    'ó',
    'ù',
    'ú',
    ]

def remove_accents(input_str):
    if input_str in allowed_characters:
        return input_str
    if input_str == 'ø':
        return 'o'
    elif input_str=='ß' or input_str =='ß':
        return 'b'
    elif input_str=='ё':
        return 'e'
    elif input_str=='đ':
        return 'd'
    nfkd_form = unicodedata.normalize('NFKD', input_str)
    only_ascii = nfkd_form.encode('ASCII', 'ignore').decode()
    
    if only_ascii is None or only_ascii=='':
        return input_str
    else:
        return only_ascii
def fix_accents(sentence):
    new_sentence=''
    for char in sentence:
        new_sentence+=remove_accents(char)
    return new_sentence

test_dataset = load_dataset("common_voice", "it", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained('gchhablani/wav2vec2-large-xlsr-it')
model = Wav2Vec2ForCTC.from_pretrained('gchhablani/wav2vec2-large-xlsr-it') 
model.to("cuda")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

chars_to_remove= [",", "?", ".", "!", "-", ";", ":", '""', "%", '"', "�",'ʿ','“','”','(','=','`','_','+','«','<','>','~','…','«','»','–','\[','\]','°','̇','´','ʾ','„','̇','̇','̇','¡'] # All extra characters

chars_to_remove_regex = f'[{"".join(chars_to_remove)}]'

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_remove_regex, '', batch["sentence"]).lower().replace('‘',"'").replace('ʻ',"'").replace('ʼ',"'").replace('’',"'").replace('ʹ',"''").replace('̇','')
    batch["sentence"] = fix_accents(batch["sentence"])
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

        pred_ids = torch.argmax(logits, dim=-1)
        batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * chunked_wer(predictions=result["pred_strings"], targets=result["sentence"],chunk_size=5000)))
```

**Test Result**: 11.49 % 

## Training

The Common Voice `train` and `validation` datasets were used for training. The code can be found [here](https://github.com/gchhablani/wav2vec2-week/blob/main/fine-tune-xlsr-wav2vec2-on-italian-asr-with-transformers_final.ipynb).