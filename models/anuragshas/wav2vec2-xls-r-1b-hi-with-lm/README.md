---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
model-index:
- name: XLS-R-1B - Hindi
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: hi
    metrics:
       - name: Test WER
         type: wer
         value: 15.899
       - name: Test CER
         type: cer
         value: 5.830
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-1B - Hindi

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6921
- Wer: 0.3547

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.0674        | 2.07  | 400  | 1.3411          | 0.8835 |
| 1.324         | 4.15  | 800  | 0.9311          | 0.7142 |
| 1.2023        | 6.22  | 1200 | 0.8060          | 0.6170 |
| 1.1573        | 8.29  | 1600 | 0.7415          | 0.4972 |
| 1.1117        | 10.36 | 2000 | 0.7248          | 0.4588 |
| 1.0672        | 12.44 | 2400 | 0.6729          | 0.4350 |
| 1.0336        | 14.51 | 2800 | 0.7117          | 0.4346 |
| 1.0025        | 16.58 | 3200 | 0.7019          | 0.4272 |
| 0.9578        | 18.65 | 3600 | 0.6792          | 0.4118 |
| 0.9272        | 20.73 | 4000 | 0.6863          | 0.4156 |
| 0.9321        | 22.8  | 4400 | 0.6535          | 0.3972 |
| 0.8802        | 24.87 | 4800 | 0.6766          | 0.3906 |
| 0.844         | 26.94 | 5200 | 0.6782          | 0.3949 |
| 0.8387        | 29.02 | 5600 | 0.6916          | 0.3921 |
| 0.8042        | 31.09 | 6000 | 0.6806          | 0.3797 |
| 0.793         | 33.16 | 6400 | 0.7120          | 0.3831 |
| 0.7567        | 35.23 | 6800 | 0.6862          | 0.3808 |
| 0.7463        | 37.31 | 7200 | 0.6893          | 0.3709 |
| 0.7053        | 39.38 | 7600 | 0.7096          | 0.3701 |
| 0.6906        | 41.45 | 8000 | 0.6921          | 0.3676 |
| 0.6891        | 43.52 | 8400 | 0.7167          | 0.3663 |
| 0.658         | 45.6  | 8800 | 0.6833          | 0.3580 |
| 0.6576        | 47.67 | 9200 | 0.6914          | 0.3569 |
| 0.6358        | 49.74 | 9600 | 0.6922          | 0.3551 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-1b-hi-with-lm --dataset mozilla-foundation/common_voice_8_0 --config hi --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-xls-r-1b-hi-with-lm"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "hi", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "तुम्हारे पास तीन महीने बचे हैं"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 26.209 | 15.899 |
