---
language:
- zh-HK
tags:
- automatic-speech-recognition
license: cc-by-sa-4.0
datasets:
- common_voice
metrics:
- cer
---

# Wav2vec2-large-xlsr-cantonese
This model was based on [wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53), finetuned using Common Voice/zh-HK/6.1.0.

The training code is similar to [user ctl](https://huggingface.co/ctl/wav2vec2-large-xlsr-cantonese), except that the number of training epochs was 80 (doubled) and fp16_backend is apex. The model was trained using a single RTX 3090 and docker image is nvidia/cuda:11.1-cudnn8-devel.

CER is 15.11% when evaluate against common voice zh-HK test set.

# Result (CER)
15.11% 

# Source Code
See this GitHub Repo [cantonese-selfish-project](https://github.com/scottykwok/cantonese-selfish-project/) and [demo video](https://youtu.be/k_9RQ-ilGEc).

# Usage
```python
import soundfile as sf
import torch
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor

# load pretrained model
processor = Wav2Vec2Processor.from_pretrained("scottykwok/wav2vec2-large-xlsr-cantonese")
model = Wav2Vec2ForCTC.from_pretrained("scottykwok/wav2vec2-large-xlsr-cantonese")

# load audio - must be 16kHz mono
audio_input, sample_rate = sf.read('audio.wav')

# pad input values and return pt tensor
input_values = processor(audio_input, sampling_rate=sample_rate, return_tensors="pt").input_values

# INFERENCE
# retrieve logits & take argmax
logits = model(input_values).logits
predicted_ids = torch.argmax(logits, dim=-1)

# transcribe
transcription = processor.decode(predicted_ids[0])
print("-" *20)
print("Transcription:\n", transcription.lower())
print("-" *20)

```
