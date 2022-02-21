---
language: ja
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
- name: XLSR Wav2Vec2 Japanese by Chien Vu
  results:
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice Japanese
      type: common_voice
      args: ja
    metrics:
       - name: Test WER
         type: wer
         value: 30.84
       - name: Test CER
         type: cer
         value: 17.85
widget:
- example_title: Japanese speech corpus sample 1
  src: https://u.pcloud.link/publink/show?code=XZwhAlXZFOtXiqKHMzmYS9wXrCP8Yb7EtRd7
- example_title: Japanese speech corpus sample 2
  src: https://u.pcloud.link/publink/show?code=XZ6hAlXZ5ccULt0YtrhJFl7LygKg0SJzKX0k
---
# Wav2Vec2-Large-XLSR-53-Japanese
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Japanese using the [Common Voice](https://huggingface.co/datasets/common_voice) and Japanese speech corpus of Saruwatari-lab, University of Tokyo [JSUT](https://sites.google.com/site/shinnosuketakamichi/publication/jsut).
When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
The model can be used directly (without a language model) as follows:
```python
!pip install mecab-python3
!pip install unidic-lite
!python -m unidic download
import torch
import torchaudio
import librosa
from datasets import load_dataset
import MeCab
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

# config
wakati = MeCab.Tagger("-Owakati")
chars_to_ignore_regex = '[\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\,\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\、\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\。\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\．\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\「\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\」\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\…\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\？\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\・]'

# load data, processor and model
test_dataset = load_dataset("common_voice", "ja", split="test[:2%]")
processor = Wav2Vec2Processor.from_pretrained("vumichien/wav2vec2-large-xlsr-japanese")
model = Wav2Vec2ForCTC.from_pretrained("vumichien/wav2vec2-large-xlsr-japanese")
resampler = lambda sr, y: librosa.resample(y.numpy().squeeze(), sr, 16_000)

# Preprocessing the datasets.
def speech_file_to_array_fn(batch):
    batch["sentence"] = wakati.parse(batch["sentence"]).strip()
    batch["sentence"] = re.sub(chars_to_ignore_regex,'', batch["sentence"]).strip()
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(sampling_rate, speech_array).squeeze()
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
The model can be evaluated as follows on the Japanese test data of Common Voice.
```python
!pip install mecab-python3
!pip install unidic-lite
!python -m unidic download

import torch
import librosa
import torchaudio
from datasets import load_dataset, load_metric
import MeCab
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

#config
wakati = MeCab.Tagger("-Owakati")
chars_to_ignore_regex = '[\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\,\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\、\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\。\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\．\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\「\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\」\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\…\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\？\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\・]'

# load data, processor and model
test_dataset = load_dataset("common_voice", "ja", split="test")
wer = load_metric("wer")
processor = Wav2Vec2Processor.from_pretrained("vumichien/wav2vec2-large-xlsr-japanese")
model = Wav2Vec2ForCTC.from_pretrained("vumichien/wav2vec2-large-xlsr-japanese")
model.to("cuda")
resampler = lambda sr, y: librosa.resample(y.numpy().squeeze(), sr, 16_000)

# Preprocessing the datasets.
def speech_file_to_array_fn(batch):
    batch["sentence"] = wakati.parse(batch["sentence"]).strip()
    batch["sentence"] = re.sub(chars_to_ignore_regex,'', batch["sentence"]).strip()
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(sampling_rate, speech_array).squeeze()
    return batch
test_dataset = test_dataset.map(speech_file_to_array_fn)

# evaluate function
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)
    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits
    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch
result = test_dataset.map(evaluate, batched=True, batch_size=8)
print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```
## Test Result
**WER:** 30.84%,
**CER:** 17.85%

## Training
The Common Voice `train`, `validation` datasets and Japanese speech corpus `basic5000` datasets were used for training.

