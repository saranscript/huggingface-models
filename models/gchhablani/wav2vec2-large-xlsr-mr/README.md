---
language: mr
datasets:
- openslr
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Large 53 Marathi by Gunjan Chhablani
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: OpenSLR mr
      type: openslr
    metrics:
       - name: Test WER
         type: wer
         value: 14.53
---

# Wav2Vec2-Large-XLSR-53-Marathi

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Marathi using the [OpenSLR SLR64](http://openslr.org/64/) dataset. Note that this data contains only female voices. Please keep this in mind before using the model for your task, although it works very well for male voice too. When using this model, make sure that your speech input is sampled at 16kHz. 

## Usage

The model can be used directly (without a language model) as follows, assuming you have a dataset with Marathi `sentence` and `path` fields:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

# test_dataset = #TODO: WRITE YOUR CODE TO LOAD THE TEST DATASET. For sample see the Colab link in Training Section.

processor = Wav2Vec2Processor.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr")
model = Wav2Vec2ForCTC.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr")

resampler = torchaudio.transforms.Resample(48_000, 16_000) # The original data was with 48,000 sampling rate. You can change it according to your input.

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

The model can be evaluated as follows on 10% of the Marathi data on OpenSLR.

```python
import torch
import torchaudio
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

# test_dataset = #TODO: WRITE YOUR CODE TO LOAD THE TEST DATASET. For sample see the Colab link in Training Section.

wer = load_metric("wer")

processor = Wav2Vec2Processor.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr")
model = Wav2Vec2ForCTC.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\%\‘\”\�\–\…]'
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
        logits = model(inputs.input_values.to("cuda"), 
        attention_mask=inputs.attention_mask.to("cuda")).logits
        pred_ids = torch.argmax(logits, dim=-1)
        batch["pred_strings"] = processor.batch_decode(pred_ids)
        return batch

result = test_dataset.map(evaluate, batched=True, batch_size=8)

print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["sentence"])))
```

**Test Result**: 14.53 %  

## Training

90% of the OpenSLR Marathi dataset was used for training.
The colab notebook used for training can be found [here](https://colab.research.google.com/drive/1_BbLyLqDUsXG3RpSULfLRjC6UY3RjwME?usp=sharing). 
