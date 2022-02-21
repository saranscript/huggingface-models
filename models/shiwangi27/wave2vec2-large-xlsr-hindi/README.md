---
language: hi
datasets:
- openslr_hindi
- common_voice
metrics:
- wer 
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week 
- xlsr-hindi
license: apache-2.0 
model-index:
- name: Fine-tuned Hindi XLSR Wav2Vec2 Large 
  results:
  - task:
      name: Speech Recognition 
      type: automatic-speech-recognition 
    datasets: 
      - name: Common Voice hi 
        type: common_voice 
        args: hi
      - name: OpenSLR Hindi
        url: https://www.openslr.org/resources/103/
    metrics:
      - name: Test WER 
        type: wer 
        value: 46.05 
---

# Wav2Vec2-Large-XLSR-Hindi

Fine-tuned facebook/wav2vec2-large-xlsr-53 on Hindi using OpenSLR Hindi dataset for training and Common Voice Hindi Test dataset for Evaluation. The OpenSLR Hindi data used for training was of size 10000 and it was randomly sampled. The OpenSLR train and test sets were combined and used as training data in order to increase the amount of variations. The evaluation was done on Common Voice Test set. The OpenSLR data is 8kHz and hence it was upsampled to 16kHz for training. 

When using this model, make sure that your speech input is sampled at 16kHz.

*Note: This is the first iteration of the fine-tuning. Will update this model if WER improves in future experiments.*

## Test Results

| Dataset | WER |
| ------- | --- |
| Test split Common Voice Hindi | 46.055 % |


## Usage 

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

test_dataset = load_dataset("common_voice", "hi", split="test[:2%]")

processor = Wav2Vec2Processor.from_pretrained("shiwangi27/wave2vec2-large-xlsr-hindi") 
model = Wav2Vec2ForCTC.from_pretrained("shiwangi27/wave2vec2-large-xlsr-hindi")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
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

The model can be evaluated as follows on the Hindi test data of Common Voice.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

test_dataset = load_dataset("common_voice", "hi", split="test") 
wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("shiwangi27/wave2vec2-large-xlsr-hindi") 
model = Wav2Vec2ForCTC.from_pretrained("shiwangi27/wave2vec2-large-xlsr-hindi") 
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\%\�\।\']'
resampler = torchaudio.transforms.Resample(48_000, 16_000)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
	batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower()
	speech_array, sampling_rate = torchaudio.load(batch["path"])
	batch["speech"] = resampler(speech_array).squeeze().numpy()
	return batch

test_dataset = test_dataset.map(speech_file_to_array_fn)

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

## Code

The Notebook used for training this model can be found at [shiwangi27/googlecolab](https://github.com/shiwangi27/googlecolab/blob/main/run_common_voice.ipynb). 
I used a modified version of [run_common_voice.py](https://github.com/shiwangi27/googlecolab/blob/main/run_common_voice.py) for training.
