---
tags:
- audio
- automatic-speech-recognition
- audio-classification
---

# Music Genre Classification using Wav2Vec 2.0


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
model_name_or_path = "m3hrdadfi/wav2vec2-base-100k-voxpopuli-gtzan-music"
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
path = "genres_original/disco/disco.00067.wav"
outputs = predict(path, sampling_rate)
```

```bash
[
{'Label': 'blues', 'Score': '0.0%'},
{'Label': 'classical', 'Score': '0.0%'},
{'Label': 'country', 'Score': '0.0%'},
{'Label': 'disco', 'Score': '99.8%'},
{'Label': 'hiphop', 'Score': '0.0%'},
{'Label': 'jazz', 'Score': '0.0%'},
{'Label': 'metal', 'Score': '0.0%'},
{'Label': 'pop', 'Score': '0.0%'},
{'Label': 'reggae', 'Score': '0.0%'},
{'Label': 'rock', 'Score': '0.0%'}
]
```


## Evaluation
The following tables summarize the scores obtained by model overall and per each class.


|     label    | precision | recall | f1-score | support |
|:------------:|:---------:|:------:|:--------:|:-------:|
|     blues    |   0.792   |  0.950 |   0.864  |    20   |
|   classical  |   0.864   |  0.950 |   0.905  |    20   |
|    country   |   0.812   |  0.650 |   0.722  |    20   |
|     disco    |   0.778   |  0.700 |   0.737  |    20   |
|    hiphop    |   0.933   |  0.700 |   0.800  |    20   |
|     jazz     |   1.000   |  0.850 |   0.919  |    20   |
|     metal    |   0.783   |  0.900 |   0.837  |    20   |
|      pop     |   0.917   |  0.550 |   0.687  |    20   |
|    reggae    |   0.543   |  0.950 |   0.691  |    20   |
|     rock     |   0.611   |  0.550 |   0.579  |    20   |
|   accuracy   |   0.775   |  0.775 |   0.775  |    0    |
|   macro avg  |   0.803   |  0.775 |   0.774  |   200   |
| weighted avg |   0.803   |  0.775 |   0.774  |   200   |


## Questions?
Post a Github issue from [HERE](https://github.com/m3hrdadfi/soxan/issues).