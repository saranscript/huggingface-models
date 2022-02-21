---
language: vi
datasets:
- vlsp
- common_voice
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
model-index:
- name: Wav2vec2 Base Vietnamese
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice vi
      type: common_voice
      args: vi
    metrics:
       - name: Test WER
         type: wer
         value: 31.353591
---
# Wav2Vec2-Large-XLSR-53-Vietnamese
Fine-tuned [dragonSwing/wav2vec2-base-pretrain-vietnamese](https://huggingface.co/dragonSwing/wav2vec2-base-pretrain-vietnamese) on Vietnamese Speech Recognition task using 100h labelled data from [VSLP dataset](https://drive.google.com/file/d/1vUSxdORDxk-ePUt-bUVDahpoXiqKchMx/view?usp=sharing).
When using this model, make sure that your speech input is sampled at 16kHz.
## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
test_dataset = load_dataset("common_voice", "vi", split="test")
processor = Wav2Vec2Processor.from_pretrained("dragonSwing/wav2vec2-base-vietnamese")
model = Wav2Vec2ForCTC.from_pretrained("dragonSwing/wav2vec2-base-vietnamese")
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
The model can be evaluated as follows on the Vietnamese test data of Common Voice.
```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re
test_dataset = load_dataset("common_voice", "vi", split="test")
wer = load_metric("wer")
processor = Wav2Vec2Processor.from_pretrained("dragonSwing/wav2vec2-base-vietnamese")
model = Wav2Vec2ForCTC.from_pretrained("dragonSwing/wav2vec2-base-vietnamese")
model.to("cuda")
chars_to_ignore_regex = r'[,?.!\-;:"“%\'�]'
resampler = torchaudio.transforms.Resample(48_000, 16_000)
# Preprocessing the datasets.
# We need to read the aduio files as arrays
def speech_file_to_array_fn(batch):
  batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
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
result = test_dataset.map(evaluate, batched=True, batch_size=1)
print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```
**Test Result**: 31.353591%
