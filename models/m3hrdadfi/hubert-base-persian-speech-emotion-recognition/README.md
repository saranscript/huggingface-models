---
language: fa
datasets:
- ShEMO
tags:
- audio
- speech
- speech-emotion-recognition
license: apache-2.0
---

# Emotion Recognition in Persian (fa) Speech using HuBERT


## How to use

### Requirements

```bash
# requirement packages
!pip install git+https://github.com/huggingface/datasets.git
!pip install git+https://github.com/huggingface/transformers.git
!pip install torchaudio
!pip install librosa
```

```bash
!git clone https://github.com/m3hrdadfi/soxan.git .
```

### Prediction

```python
import torch
import torch.nn as nn
import torch.nn.functional as F
import torchaudio
from transformers import AutoConfig, Wav2Vec2FeatureExtractor
from src.models import Wav2Vec2ForSpeechClassification, HubertForSpeechClassification

import librosa
import IPython.display as ipd
import numpy as np
import pandas as pd
```

```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model_name_or_path = "m3hrdadfi/hubert-base-persian-speech-emotion-recognition"
config = AutoConfig.from_pretrained(model_name_or_path)
feature_extractor = Wav2Vec2FeatureExtractor.from_pretrained(model_name_or_path)
sampling_rate = feature_extractor.sampling_rate
model = HubertForSpeechClassification.from_pretrained(model_name_or_path).to(device)
```

```python
def speech_file_to_array_fn(path, sampling_rate):
    speech_array, _sampling_rate = torchaudio.load(path)
    resampler = torchaudio.transforms.Resample(_sampling_rate)
    speech = resampler(speech_array).squeeze().numpy()
    return speech


def predict(path, sampling_rate):
    speech = speech_file_to_array_fn(path, sampling_rate)
    inputs = feature_extractor(speech, sampling_rate=sampling_rate, return_tensors="pt", padding=True)
    inputs = {key: inputs[key].to(device) for key in inputs}

    with torch.no_grad():
        logits = model(**inputs).logits

    scores = F.softmax(logits, dim=1).detach().cpu().numpy()[0]
    outputs = [{"Label": config.id2label[i], "Score": f"{round(score * 100, 3):.1f}%"} for i, score in enumerate(scores)]
    return outputs
```

```python
path = "/path/to/sadness.wav"
outputs = predict(path, sampling_rate)
```

```bash
[
{'Label': 'Anger', 'Score': '0.0%'},
{'Label': 'Fear', 'Score': '0.0%'},
{'Label': 'Happiness', 'Score': '0.0%'},
{'Label': 'Neutral', 'Score': '0.0%'},
{'Label': 'Sadness', 'Score': '99.9%'},
{'Label': 'Surprise', 'Score': '0.0%'}
]
```


## Evaluation
The following tables summarize the scores obtained by model overall and per each class.


|  Emotions | precision | recall | f1-score | accuracy |
|:---------:|:---------:|:------:|:--------:|:--------:|
|   Anger   |    0.96   |  0.96  |   0.96   |          |
|    Fear   |    1.00   |  0.50  |   0.67   |          |
| Happiness |    0.79   |  0.87  |   0.83   |          |
|  Neutral  |    0.93   |  0.94  |   0.93   |          |
|  Sadness  |    0.87   |  0.94  |   0.91   |          |
|  Surprise |    0.97   |  0.75  |   0.85   |          |
|           |           |        |  Overal  |   0.92   |


## Questions?
Post a Github issue from [HERE](https://github.com/m3hrdadfi/soxan/issues).