---
language: eo
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
- name: Wav2Vec2 Large 53 Esperanto by Gunjan Chhablani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice eo
      type: common_voice
      args: eo
    metrics:
       - name: Test WER
         type: wer
         value: 10.13
---

# Wav2Vec2-Large-XLSR-53-Esperanto

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Esperanto using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset. 
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "eo", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained('gchhablani/wav2vec2-large-xlsr-eo')
model = Wav2Vec2ForCTC.from_pretrained('gchhablani/wav2vec2-large-xlsr-eo')


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
    
test_dataset = load_dataset("common_voice", "eo", split="test") #TODO: replace {lang_id} in your language code here. Make sure the code is one of the *ISO codes* of [this](https://huggingface.co/languages) site.
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained('gchhablani/wav2vec2-large-xlsr-eo')
model = Wav2Vec2ForCTC.from_pretrained('gchhablani/wav2vec2-large-xlsr-eo')
model.to("cuda")

chars_to_ignore_regex = """[\\\\\\\\,\\\\\\\\?\\\\\\\\.\\\\\\\\!\\\\\\\\-\\\\\\\\;\\\\\\\\:\\\\\\\\"\\\\\\\\“\\\\\\\\%\\\\\\\\‘\\\\\\\\”\\\\\\\\�\\\\\\\\„\\\\\\\\«\\\\\\\\(\\\\\\\\»\\\\\\\\)\\\\\\\\’\\\\\\\\']"""
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace('—',' ').replace('–',' ')
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

**Test Result**: 10.13 % 

## Training

The Common Voice `train` and `validation` datasets were used for training. The code can be found [here](https://github.com/gchhablani/wav2vec2-week/blob/main/fine-tune-xlsr-wav2vec2-on-esperanto-asr-with-transformers-final.ipynb).