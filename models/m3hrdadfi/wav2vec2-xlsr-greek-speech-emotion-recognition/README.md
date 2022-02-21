---
language: el
datasets:
- aesdd
tags:
- audio
- automatic-speech-recognition
- speech
- speech-emotion-recognition
license: apache-2.0
---

# Emotion Recognition in Greek (el) Speech using Wav2Vec 2.0


## How to use

### Requirements

```bash
# requirement packages
!pip install git+https://github.com/huggingface/datasets.git
!pip install git+https://github.com/huggingface/transformers.git
!pip install torchaudio
!pip install librosa
```

### Prediction

```python
import torch
import torch.nn as nn
import torch.nn.functional as F
import torchaudio
from transformers import AutoConfig, Wav2Vec2FeatureExtractor

import librosa
import IPython.display as ipd
import numpy as np
import pandas as pd
```

```python
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model_name_or_path = "m3hrdadfi/wav2vec2-xlsr-greek-speech-emotion-recognition"
config = AutoConfig.from_pretrained(model_name_or_path)
feature_extractor = Wav2Vec2FeatureExtractor.from_pretrained(model_name_or_path)
sampling_rate = feature_extractor.sampling_rate
model = Wav2Vec2ForSpeechClassification.from_pretrained(model_name_or_path).to(device)
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
    outputs = [{"Emotion": config.id2label[i], "Score": f"{round(score * 100, 3):.1f}%"} for i, score in enumerate(scores)]
    return outputs
```

```python
path = "/path/to/disgust.wav"
outputs = predict(path, sampling_rate)
```

```bash
[
{'Emotion': 'anger', 'Score': '0.0%'},
{'Emotion': 'disgust', 'Score': '99.2%'},
{'Emotion': 'fear', 'Score': '0.1%'},
{'Emotion': 'happiness', 'Score': '0.3%'},
{'Emotion': 'sadness', 'Score': '0.5%'}
]
```


## Evaluation
The following tables summarize the scores obtained by model overall and per each class.


| Emotions  | precision | recall | f1-score | accuracy |
|-----------|-----------|--------|----------|----------|
| anger     | 0.92      | 1.00   | 0.96     |          |
| disgust   | 0.85      | 0.96   | 0.90     |          |
| fear      | 0.88      | 0.88   | 0.88     |          |
| happiness | 0.94      | 0.71   | 0.81     |          |
| sadness   | 0.96      | 1.00   | 0.98     |          |
|           |           |        | Overal   | 0.91     |


## Questions?
Post a Github issue from [HERE](https://github.com/m3hrdadfi/soxan/issues).