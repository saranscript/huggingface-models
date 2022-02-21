---
language:
- cs
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
- robust-speech-event
- xlsr-fine-tuning-week
datasets:
- common_voice
model-index:
- name: Czech comodoro Wav2Vec2 XLSR 300M CV6.1
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 6.1
      type: common_voice
      args: cs
    metrics:
       - name: Test WER
         type: wer
         value: 22.20
       - name: Test CER
         type: cer
         value: 5.1
---
# Wav2Vec2-Large-XLSR-53-Czech

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Czech using the [Common Voice](https://huggingface.co/datasets/common_voice) dataset.
When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "cs", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("comodoro/wav2vec2-xls-r-300m-cs")
model = Wav2Vec2ForCTC.from_pretrained("comodoro/wav2vec2-xls-r-300m-cs")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the aduio files as arrays
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
print("Reference:", test_dataset[:2]["sentence"])
```


## Evaluation

The model can be evaluated as follows on the Czech test data of Common Voice 6.1 


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "cs", split="test") 
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("comodoro/wav2vec2-xls-r-300m-cs")
model = Wav2Vec2ForCTC.from_pretrained("comodoro/wav2vec2-xls-r-300m-cs") 
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\/\"\“\„\%\”\�\–\'\`\«\»\—\’\…]'
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

**Test Result**: 22.20 % 


## Training

The Common Voice `train` and `validation` datasets were used for training

# TODO The script used for training can be found [here](...)