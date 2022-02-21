---
tags:
- audio
- automatic-speech-recognition
- audio-classification
---

# Eating Sound Classification using Wav2Vec 2.0


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
model_name_or_path = "m3hrdadfi/wav2vec2-base-100k-eating-sound-collection"
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
    outputs = [{"Label": config.id2label[i], "Score": f"{round(score * 100, 3):.1f}%"} for i, score in enumerate(scores)]
    return outputs
```

```python
path = "clips_rd/gummies/gummies_6_04.wav"
outputs = predict(path, sampling_rate)
```

```bash
[
{'Label': 'aloe', 'Score': '0.0%'},
{'Label': 'burger', 'Score': '0.0%'},
{'Label': 'cabbage', 'Score': '0.0%'},
{'Label': 'candied_fruits', 'Score': '0.0%'},
{'Label': 'carrots', 'Score': '0.0%'},
{'Label': 'chips', 'Score': '0.0%'},
{'Label': 'chocolate', 'Score': '0.0%'},
{'Label': 'drinks', 'Score': '0.0%'},
{'Label': 'fries', 'Score': '0.0%'},
{'Label': 'grapes', 'Score': '0.0%'},
{'Label': 'gummies', 'Score': '99.8%'},
{'Label': 'ice-cream', 'Score': '0.0%'},
{'Label': 'jelly', 'Score': '0.1%'},
{'Label': 'noodles', 'Score': '0.0%'},
{'Label': 'pickles', 'Score': '0.0%'},
{'Label': 'pizza', 'Score': '0.0%'},
{'Label': 'ribs', 'Score': '0.0%'},
{'Label': 'salmon', 'Score': '0.0%'},
{'Label': 'soup', 'Score': '0.0%'},
{'Label': 'wings', 'Score': '0.0%'}
]
```


## Evaluation
The following tables summarize the scores obtained by model overall and per each class.


|      label     | precision | recall | f1-score | support |
|:--------------:|:---------:|:------:|:--------:|:-------:|
|      aloe      |   0.989   |  0.807 |   0.889  |   109   |
|     burger     |   1.000   |  0.471 |   0.640  |   119   |
|     cabbage    |   0.907   |  0.970 |   0.937  |   100   |
| candied_fruits |   0.952   |  0.988 |   0.970  |   161   |
|     carrots    |   0.970   |  0.992 |   0.981  |   132   |
|      chips     |   0.993   |  0.951 |   0.972  |   144   |
|    chocolate   |   0.828   |  0.914 |   0.869  |    58   |
|     drinks     |   0.982   |  0.948 |   0.965  |    58   |
|      fries     |   0.935   |  0.783 |   0.852  |   129   |
|     grapes     |   0.965   |  0.940 |   0.952  |   116   |
|     gummies    |   0.880   |  0.971 |   0.923  |   136   |
|    ice-cream   |   0.953   |  0.972 |   0.962  |   145   |
|      jelly     |   0.906   |  0.875 |   0.890  |    88   |
|     noodles    |   0.817   |  0.817 |   0.817  |    82   |
|     pickles    |   0.933   |  0.960 |   0.946  |   174   |
|      pizza     |   0.704   |  0.934 |   0.803  |   122   |
|      ribs      |   0.796   |  0.755 |   0.775  |    98   |
|     salmon     |   0.647   |  0.970 |   0.776  |   100   |
|      soup      |   0.941   |  0.857 |   0.897  |    56   |
|      wings     |   0.842   |  0.792 |   0.816  |   101   |
|    accuracy    |   0.890   |  0.890 |   0.890  |    0    |
|    macro avg   |   0.897   |  0.883 |   0.882  |   2228  |
|  weighted avg  |   0.903   |  0.890 |   0.888  |   2228  |


## Questions?
Post a Github issue from [HERE](https://github.com/m3hrdadfi/soxan/issues).