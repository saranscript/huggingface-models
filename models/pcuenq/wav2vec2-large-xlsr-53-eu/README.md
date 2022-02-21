---
language: eu
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
- name: XLSR Wav2Vec2 Large 53 Basque by pcuenq 
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice eu
      type: common_voice
      args: eu
    metrics:
       - name: Test WER
         type: wer
         value: 15.34
---

# Wav2Vec2-Large-XLSR-53-EU

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Basque using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "eu", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("pcuenq/wav2vec2-large-xlsr-53-eu")
model = Wav2Vec2ForCTC.from_pretrained("pcuenq/wav2vec2-large-xlsr-53-eu")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
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

The model can be evaluated as follows on the Basque test data of Common Voice.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "eu", split="test")
wer = load_metric("wer")

model_name = "pcuenq/wav2vec2-large-xlsr-53-eu"

processor = Wav2Vec2Processor.from_pretrained(model_name)
model = Wav2Vec2ForCTC.from_pretrained(model_name)
model.to("cuda")

## Text pre-processing

chars_to_ignore_regex = '[\,\¿\?\.\¡\!\-\;\:\"\“\%\‘\”\￼\…\’\ː\'\‹\›\`\´\®\—\→]'
chars_to_ignore_pattern = re.compile(chars_to_ignore_regex)

def remove_special_characters(batch):
    batch["sentence"] = chars_to_ignore_pattern.sub('', batch["sentence"]).lower() + " "
    return batch

## Audio pre-processing

import librosa
def speech_file_to_array_fn(batch):
    speech_array, sample_rate = torchaudio.load(batch["path"])
    batch["speech"] = librosa.resample(speech_array.squeeze().numpy(), sample_rate, 16_000)
    return batch

# Text transformation and audio resampling
def cv_prepare(batch):
    batch = remove_special_characters(batch)
    batch = speech_file_to_array_fn(batch)
    return batch

# Number of CPUs or None
num_proc = 16
test_dataset = test_dataset.map(cv_prepare, remove_columns=['path'], num_proc=num_proc)

def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)

    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits

    pred_ids = torch.argmax(logits, dim=-1)
    batch["pred_strings"] = processor.batch_decode(pred_ids)
    return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

# WER Metric computation
print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 15.34 %

## Training

The Common Voice `train` and `validation` datasets were used for training. Training was performed for 22 + 20 epochs with the following parameters:

- Batch size 16, 2 gradient accumulation steps.
- Learning rate: 2.5e-4
- Activation dropout: 0.05
- Attention dropout: 0.1
- Hidden dropout: 0.05
- Feature proj. dropout: 0.05
- Mask time probability: 0.08
- Layer dropout: 0.05

