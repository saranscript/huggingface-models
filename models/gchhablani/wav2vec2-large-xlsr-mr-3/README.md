---
language: mr
datasets:
- openslr
- interspeech_2021_asr
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
      name: OpenSLR mr, InterSpeech 2021 ASR mr
      type: openslr, interspeech_2021_asr
    metrics:
       - name: Test WER
         type: wer
         value: 19.05
---

# Wav2Vec2-Large-XLSR-53-Marathi

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Marathi using the [OpenSLR SLR64](http://openslr.org/64/) dataset and [InterSpeech 2021](https://navana-tech.github.io/IS21SS-indicASRchallenge/data.html) Marathi datasets. Note that this data OpenSLR contains only female voices. Please keep this in mind before using the model for your task. When using this model, make sure that your speech input is sampled at 16kHz. 

## Usage

The model can be used directly (without a language model) as follows, assuming you have a dataset with Marathi `text` and `audio_path` fields:

```python
import torch
import torchaudio
import librosa
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

# test_data = #TODO: WRITE YOUR CODE TO LOAD THE TEST DATASET. For sample see the Colab link in Training Section.

processor = Wav2Vec2Processor.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr-3")
model = Wav2Vec2ForCTC.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr-3")

# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    speech_array, sampling_rate = torchaudio.load(batch["audio_path"])
    batch["speech"] = librosa.resample(speech_array[0].numpy(), sampling_rate, 16_000) # sampling_rate can vary
    return batch

test_data= test_data.map(speech_file_to_array_fn)
inputs = processor(test_data["speech"][:2], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values, attention_mask=inputs.attention_mask).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
print("Reference:", test_data["text"][:2])
```


## Evaluation

The model can be evaluated as follows on 10% of the Marathi data on OpenSLR.

```python
import torch
import torchaudio
import librosa
from datasets import load_dataset, load_metric
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
import re

# test_data = #TODO: WRITE YOUR CODE TO LOAD THE TEST DATASET. For sample see the Colab link in Training Section.

wer = load_metric("wer")
processor = Wav2Vec2Processor.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr-3")
model = Wav2Vec2ForCTC.from_pretrained("gchhablani/wav2vec2-large-xlsr-mr-3")
model.to("cuda")

chars_to_ignore_regex = '[\,\?\.\!\-\;\:\"\“\%\‘\”\�\–\…]'


# Preprocessing the datasets.
# We need to read the audio files as arrays
def speech_file_to_array_fn(batch):
    batch["text"] = re.sub(chars_to_ignore_regex, '', batch["text"]).lower()
    speech_array, sampling_rate = torchaudio.load(batch["audio_path"])
    batch["speech"] = librosa.resample(speech_array[0].numpy(), sampling_rate, 16_000)
    return batch

test_data= test_data.map(speech_file_to_array_fn)

# Preprocessing the datasets.
# We need to read the audio files as arrays
def evaluate(batch):
    inputs = processor(batch["speech"], sampling_rate=16_000, return_tensors="pt", padding=True)
    with torch.no_grad():
        logits = model(inputs.input_values.to("cuda"), attention_mask=inputs.attention_mask.to("cuda")).logits
        pred_ids = torch.argmax(logits, dim=-1)
        batch["pred_strings"] = processor.batch_decode(pred_ids)
        return batch

result = test_data.map(evaluate, batched=True, batch_size=8)
print("WER: {:2f}".format(100 * wer.compute(predictions=result["pred_strings"], references=result["text"])))
```

**Test Result**: 19.05 % (157+157 examples)
 
**Test Result on OpenSLR test**: 14.15 % (157 examples)

**Test Results on InterSpeech test**: 27.14 % (157 examples)

## Training

1412 examples of the OpenSLR Marathi dataset  and 1412 examples of InterSpeech 2021 Marathi ASR dataset were used for training. For testing, 157 examples from each were used.

The colab notebook used for training and evaluation can be found [here](https://colab.research.google.com/drive/15fUhb4bUFFGJyNLr-_alvPxVX4w0YXRu?usp=sharing). 
