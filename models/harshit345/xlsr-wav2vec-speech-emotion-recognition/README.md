---
language: en
datasets:
- aesdd
tags:
- audio
- audio-classification
- speech
license: apache-2.0
---
~~~
# requirement packages
!pip install git+https://github.com/huggingface/datasets.git
!pip install git+https://github.com/huggingface/transformers.git
!pip install torchaudio
!pip install librosa

~~~
# prediction
~~~
import torch
import torch.nn as nn
import torch.nn.functional as F
import torchaudio
from transformers import AutoConfig, Wav2Vec2FeatureExtractor
import librosa
import IPython.display as ipd
import numpy as np
import pandas as pd
~~~
~~~
device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
model_name_or_path = "harshit345/xlsr-wav2vec-speech-emotion-recognition"
config = AutoConfig.from_pretrained(model_name_or_path)
feature_extractor = Wav2Vec2FeatureExtractor.from_pretrained(model_name_or_path)
sampling_rate = feature_extractor.sampling_rate
model = Wav2Vec2ForSpeechClassification.from_pretrained(model_name_or_path).to(device)
~~~
~~~
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
~~~
# prediction
~~~
# path for a sample
path = '/data/jtes_v1.1/wav/f01/ang/f01_ang_01.wav'   
outputs = predict(path, sampling_rate)
~~~
~~~
[{'Emotion': 'anger', 'Score': '78.3%'},
 {'Emotion': 'disgust', 'Score': '11.7%'},
 {'Emotion': 'fear', 'Score': '5.4%'},
 {'Emotion': 'happiness', 'Score': '4.1%'},
 {'Emotion': 'sadness', 'Score': '0.5%'}]
 ~~~
 
 ## Evaluation
The following tables summarize the scores obtained by model overall and per each class.


| Emotions  | precision | recall | f1-score | accuracy |
|-----------|-----------|--------|----------|----------|
| anger     | 0.82      | 1.00   | 0.81     |          |
| disgust   | 0.85      | 0.96   | 0.85     |          |
| fear      | 0.78      | 0.88   | 0.80     |          |
| happiness | 0.84      | 0.71   | 0.78     |          |
| sadness   | 0.86      | 1.00   | 0.79     |          |
|           |           |        | Overall  | 0.806    |


## 
Colab Notebook
https://colab.research.google.com/drive/1aPPb_ZVS5dlFVZySly8Q80a44La1XjJu?usp=sharing