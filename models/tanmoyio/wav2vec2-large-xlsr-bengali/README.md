---
language: Bengali
datasets:
- OpenSLR
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: cc-by-sa-4.0
model-index:
- name: XLSR Wav2Vec2 Bengali by Tanmoy Sarkar
  results:
  - task:
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: OpenSLR
      type: OpenSLR
      args: ben
    metrics:
    - name: Test WER
      type: wer
      value: 88.58
---
# Wav2Vec2-Large-XLSR-Bengali
Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) Bengali using the [Bengali ASR training data set containing ~196K utterances](https://www.openslr.org/53/).
When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
Dataset must be downloaded from [this website](https://www.openslr.org/53/) and preprocessed accordingly. For example 1250 test samples has been chosen.
```python
import pandas as pd
test_dataset = pd.read_csv('utt_spk_text.tsv', sep='\\t', header=None)[60000:61250]
test_dataset.columns = ["audio_path", "__", "label"]
test_dataset = test_data.drop("__", axis=1)
def add_file_path(text):
  path = "data/" + text[:2] + "/" + text + '.flac'
  return path
test_dataset['audio_path'] = test_dataset['audio_path'].map(lambda x: add_file_path(x))
```
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
processor = Wav2Vec2Processor.from_pretrained("tanmoyio/wav2vec2-large-xlsr-bengali")
model = Wav2Vec2ForCTC.from_pretrained("tanmoyio/wav2vec2-large-xlsr-bengali")
resampler = torchaudio.transforms.Resample(48_000, 16_000)
# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
  speech_array, sampling_rate = torchaudio.load(batch["audio_path"])
  batch["speech"] = resampler(speech_array).squeeze().numpy()
  return batch
test_dataset = test_dataset.map(speech_file_to_array_fn)
inputs = processor(test_dataset["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)
with torch.no_grad():
  logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits
predicted_ids = torch.argmax(logits, dim=-1)
print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_dataset["label"][:2])
```
## Evaluation
The model can be evaluated as follows on the Bengali test data of OpenSLR.  
```python
import torch
import torchaudio
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
wer = load_metric("wer")
processor = Wav2Vec2Processor.from_pretrained("tanmoyio/wav2vec2-large-xlsr-bengali")
model = Wav2Vec2ForCTC.from_pretrained("tanmoyio/wav2vec2-large-xlsr-bengali")
model.to("cuda")
resampler = torchaudio.transforms.Resample(48_000, 16_000)
# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
  batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["label"]).lower()
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
print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```
**Test Result**: 88.58 %
## Training
The script used for training can be found [Bengali ASR Fine Tuning Wav2Vec2](https://colab.research.google.com/drive/1Bkc5C_cJV9BeS0FD0MuHyayl8hqcbdRZ?usp=sharing)
