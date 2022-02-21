---
language: lt
datasets:
- common_voice
metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
license: apache-2.0
model-index:
- name: XLSR Wav2Vec2 Lithuanian by Seçilay KUTAL
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Common Voice lt
      type: common_voice
      args: lt
    metrics:
       - name: Test WER
         type: wer
         
---
# wav2vec-lt-lite
## Usage
The model can be used directly (without a language model) as follows:
```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor
test_dataset = load_dataset("common_voice", "lt", split="test[:2%]") 
processor = Wav2Vec2Processor.from_pretrained("seccily/wav2vec-lt-lite")
model = Wav2Vec2ForCTC.from_pretrained("seccily/wav2vec-lt-lite")
resampler = torchaudio.transforms.Resample(48_000, 16_000)
```
Test Result: 59.47