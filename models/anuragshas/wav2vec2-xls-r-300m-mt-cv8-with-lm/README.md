---
language:
- mt
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
- name: XLS-R-300M - Maltese
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice 8
      args: mt
    metrics:
      - type: wer    # Required. Example: wer
        value: 15.967  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 3.657
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Maltese

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - MT dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1895
- Wer: 0.1984

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 60.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.4219        | 3.6   | 400  | 3.3127          | 1.0    |
| 3.0399        | 7.21  | 800  | 3.0330          | 1.0    |
| 1.5756        | 10.81 | 1200 | 0.6108          | 0.5724 |
| 1.0995        | 14.41 | 1600 | 0.3091          | 0.3154 |
| 0.9639        | 18.02 | 2000 | 0.2596          | 0.2841 |
| 0.9032        | 21.62 | 2400 | 0.2270          | 0.2514 |
| 0.8145        | 25.23 | 2800 | 0.2172          | 0.2483 |
| 0.7845        | 28.83 | 3200 | 0.2084          | 0.2333 |
| 0.7694        | 32.43 | 3600 | 0.1974          | 0.2234 |
| 0.7333        | 36.04 | 4000 | 0.2020          | 0.2185 |
| 0.693         | 39.64 | 4400 | 0.1947          | 0.2148 |
| 0.6802        | 43.24 | 4800 | 0.1960          | 0.2102 |
| 0.667         | 46.85 | 5200 | 0.1904          | 0.2072 |
| 0.6486        | 50.45 | 5600 | 0.1881          | 0.2009 |
| 0.6339        | 54.05 | 6000 | 0.1877          | 0.1989 |
| 0.6254        | 57.66 | 6400 | 0.1893          | 0.2003 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-mt-cv8-with-lm --dataset mozilla-foundation/common_voice_8_0 --config mt --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-xls-r-300m-mt-cv8-with-lm"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "mt", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "għadu jilagħbu ċirku tant bilfondi"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 19.853 | 15.967 |