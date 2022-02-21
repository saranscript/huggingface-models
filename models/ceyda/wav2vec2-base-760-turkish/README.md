---
language: tr
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
- name: Wav2Vec2-Base Turkish by Ceyda Cinarel
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice tr
      type: common_voice
      args: tr 
    metrics:
       - name: Test WER
         type: wer
         value: 22.60
---

# Wav2Vec2-Base-760-Turkish

# TBA
Pretrained Turkish model [ceyda/wav2vec2-base-760](https://huggingface.co/ceyda/wav2vec2-base-760). Fine-tuned on Turkish using the [Common Voice](https://huggingface.co/datasets/common_voice)
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "tr", split="test[:2%]") 

processor = Wav2Vec2Processor.from_pretrained("ceyda/wav2vec2-base-960-turkish")
model = Wav2Vec2ForCTC.from_pretrained("ceyda/wav2vec2-base-960-turkish")

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

The model can be evaluated as follows on the Turkish test data of Common Voice.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "tr", split="test")
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("ceyda/wav2vec2-base-960-turkish")
model = Wav2Vec2ForCTC.from_pretrained("ceyda/wav2vec2-base-960-turkish")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\‘\”\'\`…\’»«]'
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
    speech_array, sampling_rate = torchaudio.load(batch["path"])
    batch["speech"] = resampler(speech_array).squeeze().numpy()
    return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the aduio files as arrays

#Attention mask is not used because the base-model was not trained with it. reference: https://github.com/huggingface/transformers/blob/403d530eec105c0e229fc2b754afdf77a4439def/src/transformers/models/wav2vec2/tokenization_wav2vec2.py#L305
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids,skip_special_tokens=True)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Results**: 
- WER: 22.602390
- CER: 6.054137


## Training

The Common Voice `train`, `validation` datasets were used for training.

The script used for training can be found [here](https://github.com/cceyda/wav2vec2)