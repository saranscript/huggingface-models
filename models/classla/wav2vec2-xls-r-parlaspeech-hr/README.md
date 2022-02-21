---
language: hr
datasets:
- parlaspeech-hr
tags:
- audio
- automatic-speech-recognition
- parlaspeech
widget:
- example_title: example 1
  src: https://huggingface.co/classla/wav2vec2-xls-r-parlaspeech-hr/raw/main/SBiNG.wav
- example_title: example 2
  src: https://huggingface.co/classla/wav2vec2-xls-r-parlaspeech-hr/raw/main/00020578b.flac.wav

---

# wav2vec2-xls-r-parlaspeech-hr

This model for Croatian ASR is based on the [facebook/wav2vec2-xls-r-300m model](https://huggingface.co/facebook/wav2vec2-xls-r-300m) and was fine-tuned with 72 hours of recordings and transcripts from the Croatian parliament. This training dataset is an early result of the second iteration of the [ParlaMint project](https://www.clarin.eu/content/parlamint-towards-comparable-parliamentary-corpora) inside which the dataset will be extended and published under the name of ParlaSpeech-HR and an open licence.

The efforts resulting in this model were coordinated by Nikola Ljubešić, the rough manual data alignment was performed by Ivo-Pavao Jazbec, the method for fine automatic data alignment from [Plüss et al.](https://arxiv.org/abs/2010.02810) was applied by Vuk Batanović and Lenka Bajčetić, the transcripts were normalised by Danijel Korzinek, while the final modelling was performed by Peter Rupnik.

Initial evaluation on partially noisy data showed the model to achieve a word error rate of 13.68% and a character error rate of 4.56%.

## Usage in `transformers`

```python
from transformers import Wav2Vec2Processor, Wav2Vec2ForCTC
from datasets import Audio
import soundfile as sf
import torch
import os

# load model and tokenizer
processor = Wav2Vec2Processor.from_pretrained(
    "classla/wav2vec2-xls-r-parlaspeech-hr")
model = Wav2Vec2ForCTC.from_pretrained("classla/wav2vec2-xls-r-parlaspeech-hr")


# download the example wav files:
os.system("curl https://huggingface.co/classla/wav2vec2-xls-r-parlaspeech-hr/raw/main/00020570a.flac.wav")

# read the wav file as datasets.Audio object
audio = Audio(sampling_rate=16000).decode_example("00020570a.flac.wav")

# remove the raw wav file
os.system("rm 00020570a.flac.wav")

# tokenize
input_values = processor(
        audio["array"],  return_tensors="pt", padding=True,
        sampling_rate=16000).input_values
        
# retrieve logits
logits = model(input_values).logits

# take argmax and decode
predicted_ids = torch.argmax(logits, dim=-1)
transcription = processor.batch_decode(predicted_ids)


# transcription: ['veliki broj poslovnih subjekata posluje sa minusom velik dio']
```

## Training hyperparameters

In fine-tuning, the following arguments were used:

| arg                           | value |
|-------------------------------|-------|
| `per_device_train_batch_size` | 16    |
| `gradient_accumulation_steps` | 4     |
| `num_train_epochs`            | 8     |
| `learning_rate`               | 3e-4  |
| `warmup_steps`                | 500   |