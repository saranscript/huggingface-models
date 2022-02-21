
---
language: nah specifically ncj
datasets:
- created a new dataset based on https://www.openslr.org/92/
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: Nahuatl XLSR Wav2Vec 53
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    metrics:
       - name: Test WER
         type: wer
         value: 69.11
---

# Wav2Vec2-Large-XLSR-53-ncj/nah

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Nahuatl specifically of the Nort of Puebla (ncj) using a derivate of [SLR92](https://www.openslr.org/92/), and some samples of `es` and `de` datasets from [Common Voice](https://huggingface.co/datasets/common_voice).

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "{lang_id}", split="test[:2%]") # TODO: publish nahuatl_slr92_by_sentence

processor = Wav2Vec2Processor.from_pretrained("tyoc213/wav2vec2-large-xlsr-nahuatl")
model = Wav2Vec2ForCTC.from_pretrained("tyoc213/wav2vec2-large-xlsr-nahuatl")

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

The model can be evaluated as follows on the Nahuatl specifically of the Nort of Puebla (ncj) test data of Common Voice.


```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "{lang_id}", split="test") # TODO: publish nahuatl_slr92_by_sentence
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("tyoc213/wav2vec2-large-xlsr-nahuatl")
model = Wav2Vec2ForCTC.from_pretrained("tyoc213/wav2vec2-large-xlsr-nahuatl")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\"\“\%\‘\”\�\(\)\-]'
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

**Test Result**: 50.95 %


## Training

A derivate of [SLR92](https://www.openslr.org/92/) to be published soon.And some samples of `es` and `de` datasets from [Common Voice](https://huggingface.co/datasets/common_voice)

The script used for training can be found [less60wer.ipynb](./less60wer.ipynb)
