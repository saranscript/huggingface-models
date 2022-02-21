---
language: 
- sv-SE

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
- name: wav2vec2-large-xls-r-1b-Swedish
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice sv-SE # Required. Example: Common Voice zh-CN
      args: sv-SE       # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 14.04  # Required. Example: 20.90
        name: Test WER With LM   # Optional. Example: Test WER
        args: 
        - learning_rate: 7.5e-05
        - train_batch_size: 32
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 4
        - total_train_batch_size: 128
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 1000
        - num_epochs: 50
        - mixed_precision_training: Native AMP    # Optional. Example for BLEU: max_order
      - type: cer    # Required. Example: wer
        value: 4.86  # Required. Example: 20.90
        name: Test CER  With LM   # Optional. Example: Test WER
        args: 
        - learning_rate: 7.5e-05
        - train_batch_size: 32
        - eval_batch_size: 8
        - seed: 42
        - gradient_accumulation_steps: 4
        - total_train_batch_size: 128
        - optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
        - lr_scheduler_type: linear
        - lr_scheduler_warmup_steps: 1000
        - num_epochs: 50
        - mixed_precision_training: Native AMP
  - task: 
     name: Automatic Speech Recognition
     type: automatic-speech-recognition
    dataset:
       name: Robust Speech Event - Dev Data
       type: speech-recognition-community-v2/dev_data
       args: sv
    metrics:
        - name: Test WER
          type: wer
          value: 29.69
        - name: Test CER
          type: cer
          value: 12.59
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-1b-Swedish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the common_voice dataset.
It achieves the following results on the evaluation set:

**Without LM**
- Loss: 0.3370
- Wer: 18.44 
- Cer: 5.75

**With LM**
- Loss: 0.3370
- Wer: 14.04 
- Cer: 4.86

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xls-r-1b-Swedish --dataset mozilla-foundation/common_voice_8_0 --config sv-SE --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xls-r-1b-Swedish --dataset speech-recognition-community-v2/dev_data --config sv --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "kingabzpro/wav2vec2-large-xls-r-1b-Swedish"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "sv-SE", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
```

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 256
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 3.1562        | 11.11 | 500  | 0.4830          | 0.3729 | 0.1169 |
| 0.5655        | 22.22 | 1000 | 0.3553          | 0.2381 | 0.0743 |
| 0.3376        | 33.33 | 1500 | 0.3359          | 0.2179 | 0.0696 |
| 0.2419        | 44.44 | 2000 | 0.3232          | 0.1844 | 0.0575 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
