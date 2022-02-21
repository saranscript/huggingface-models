# Wav2Vec2-Large-XLSR-53

---
language: gl
datasets:
- OpenSLR 77
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: Galician Wav2Vec2-Large-XLSR-53
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: OpenSLR
      type: openslr
      args: gl
    metrics:
       - name: Test WER
         type: wer
         value: 16.79
---

Wav2Vec2-Large-XLSR-53-galician

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on galician using the [OpenSLR](https://huggingface.co/datasets/common_voice) dataset

When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "gl", split="test[:2%]")  # This is not available yet, load OpenSLR or your dataset instead

processor = Wav2Vec2Processor.from_pretrained("diego-fustes/wav2vec2-large-xlsr-gl")
model = Wav2Vec2ForCTC.from_pretrained("diego-fustes/wav2vec2-large-xlsr-gl")

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

The model can be evaluated as follows on the Galician test data of Common Voice (when it is released).

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "gl", split="test")   # This is not available yet, load OpenSLR or your dataset instead
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("diego-fustes/wav2vec2-large-xlsr-gl")
model = Wav2Vec2ForCTC.from_pretrained("diego-fustes/wav2vec2-large-xlsr-gl")
model.to("cuda")

chars_to_ignore_regex = '[^a-záéíóúñ ]'
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

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 16.79 % on OpenSLR split


## Training

The OpenSLR [SLR77](https://openslr.org/77/) dataset was used for training and validation. The dataset was split as 70% for training, 15% for validation and 15% for testing  

The script used for training can be found [here](https://github.com/diego-fustes/xlsr-fine-tuning-gl)
