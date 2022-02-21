---
language: 
- ar

license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
- cer
model-index:
- name: Sinai Voice Arabic Speech Recognition Model
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice ar
      args: ar
    metrics:
      - type: wer
        value: 0.181
        name: Test WER
        
      - type: cer
        value: 0.049
        name: Test CER
widget:
- example_title: Example 1
  src: https://huggingface.co/bakrianoo/sinai-voice-ar-stt/raw/main/examples/common_voice_ar_19077324.mp3
- example_title: Example 2
  src: https://huggingface.co/bakrianoo/sinai-voice-ar-stt/raw/main/examples/common_voice_ar_19205138.mp3
- example_title: Example 3
  src: https://huggingface.co/bakrianoo/sinai-voice-ar-stt/raw/main/examples/common_voice_ar_19331711.mp3        
---
<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Sinai Voice Arabic Speech Recognition Model

# نموذج **صوت سيناء** للتعرف على الأصوات العربية الفصحى و تحويلها إلى نصوص

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - AR dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2141
- Wer: 0.1808

It achieves the following results on the evaluation set:
- eval_loss               =     0.2141
- eval_samples            =      10388
- eval_wer                =     0.181
- eval_cer                =     0.049

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id bakrianoo/sinai-voice-ar-stt --dataset mozilla-foundation/common_voice_8_0 --config ar --split test
```


### Inference Without LM

```python
from transformers import (Wav2Vec2Processor, Wav2Vec2ForCTC)
import torchaudio
import torch

def speech_file_to_array_fn(voice_path, resampling_to=16000):
    speech_array, sampling_rate = torchaudio.load(voice_path)
    resampler = torchaudio.transforms.Resample(sampling_rate, resampling_to)
    
    return resampler(speech_array)[0].numpy(), sampling_rate

# load the model
cp = "bakrianoo/sinai-voice-ar-stt"
processor = Wav2Vec2Processor.from_pretrained(cp)
model = Wav2Vec2ForCTC.from_pretrained(cp)

# recognize the text in a sample sound file
sound_path = './my_voice.mp3'

sample, sr = speech_file_to_array_fn(sound_path)
inputs = processor([sample], sampling_rate=16_000, return_tensors="pt", padding=True)

with torch.no_grad():
    logits = model(inputs.input_values,).logits

predicted_ids = torch.argmax(logits, dim=-1)

print("Prediction:", processor.batch_decode(predicted_ids))
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 32
- eval_batch_size: 10
- seed: 42
- distributed_type: multi-GPU
- num_devices: 8
- total_train_batch_size: 256
- total_eval_batch_size: 80
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 10
- mixed_precision_training: Native AMP


### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.354         | 0.64  | 1000  | 0.4109          | 0.4493 |
| 0.5886        | 1.28  | 2000  | 0.2798          | 0.3099 |
| 0.4977        | 1.92  | 3000  | 0.2387          | 0.2673 |
| 0.4253        | 2.56  | 4000  | 0.2266          | 0.2523 |
| 0.3942        | 3.2   | 5000  | 0.2171          | 0.2437 |
| 0.3619        | 3.84  | 6000  | 0.2076          | 0.2253 |
| 0.3245        | 4.48  | 7000  | 0.2088          | 0.2186 |
| 0.308         | 5.12  | 8000  | 0.2086          | 0.2206 |
| 0.2881        | 5.76  | 9000  | 0.2089          | 0.2105 |
| 0.2557        | 6.4   | 10000 | 0.2015          | 0.2004 |
| 0.248         | 7.04  | 11000 | 0.2044          | 0.1953 |
| 0.2251        | 7.68  | 12000 | 0.2058          | 0.1932 |
| 0.2052        | 8.32  | 13000 | 0.2117          | 0.1878 |
| 0.1976        | 8.96  | 14000 | 0.2104          | 0.1825 |
| 0.1845        | 9.6   | 15000 | 0.2156          | 0.1821 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0