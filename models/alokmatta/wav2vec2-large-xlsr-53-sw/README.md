---
language: sw  
datasets:
- ALFFA,Gamayun & IWSLT

metrics:
- wer
tags:
- audio
- automatic-speech-recognition
- speech
- xlsr-fine-tuning-week
license: apache-2.0
model-index:
- name: Swahili XLSR-53 Wav2Vec2.0 Large
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: ALFFA sw
      args: sw
    metrics:
       - name: Test WER
         type: wer
         value: WIP
---

# Wav2Vec2-Large-XLSR-53-Swahili 

Fine-tuned [facebook/wav2vec2-large-xlsr-53](https://huggingface.co/facebook/wav2vec2-large-xlsr-53) on Swahili using the following datasets:
- [ALFFA](http://www.openslr.org/25/),
- [Gamayun](https://gamayun.translatorswb.org/download/gamayun-5k-english-swahili/) 
- [IWSLT](https://iwslt.org/2021/low-resource)

When using this model, make sure that your speech input is sampled at 16kHz.

## Usage

The model can be used directly (without a language model) as follows:

```python
import torch
import torchaudio
from datasets import load_dataset
from transformers import Wav2Vec2ForCTC, Wav2Vec2Processor


processor = Wav2Vec2Processor.from_pretrained("alokmatta/wav2vec2-large-xlsr-53-sw")

model = Wav2Vec2ForCTC.from_pretrained("alokmatta/wav2vec2-large-xlsr-53-sw").to("cuda")

resampler = torchaudio.transforms.Resample(48_000, 16_000)

resampler = torchaudio.transforms.Resample(orig_freq=48_000, new_freq=16_000)

def load_file_to_data(file):
    batch = {}
    speech, _ = torchaudio.load(file)
    batch["speech"] = resampler.forward(speech.squeeze(0)).numpy()
    batch["sampling_rate"] = resampler.new_freq
    return batch


def predict(data):
    features = processor(data["speech"], sampling_rate=data["sampling_rate"], padding=True, return_tensors="pt")
    input_values = features.input_values.to("cuda")
    attention_mask = features.attention_mask.to("cuda")
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
    pred_ids = torch.argmax(logits, dim=-1)
    return processor.batch_decode(pred_ids)

predict(load_file_to_data('./demo.wav'))
```

**Test Result**: 40 % 


## Training


The script used for training can be found [here](https://colab.research.google.com/drive/1_RL6TQv_Yiu_xbWXu4ycbzdCdXCqEQYU?usp=sharing)