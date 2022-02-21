---
language: 
- tt 

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
- name: wav2vec2-large-xls-r-300m-Tatar
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice tt # Required. Example: Common Voice zh-CN
      args: tt        # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 42.71 # Required. Example: 20.90
        name: Test WER With LM   # Optional. Example: Test WER
        
      - type: cer    # Required. Example: wer
        value: 11.18  # Required. Example: 20.90
        name: Test CER With LM   # Optional. Example: Test WER
        
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-Tatar

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5068
- Wer: 0.4263
- Cer: 0.1117

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xls-r-300m-Tatar --dataset mozilla-foundation/common_voice_8_0 --config tt --split test
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "kingabzpro/wav2vec2-large-xls-r-300m-Tatar"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "tt", split="test", streaming=True, use_auth_token=True))
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
| 8.4116        | 12.19 | 500  | 3.4118          | 1.0    | 1.0    |
| 2.5829        | 24.39 | 1000 | 0.7150          | 0.6151 | 0.1582 |
| 0.4492        | 36.58 | 1500 | 0.5378          | 0.4577 | 0.1210 |
| 0.3007        | 48.77 | 2000 | 0.5068          | 0.4263 | 0.1117 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
