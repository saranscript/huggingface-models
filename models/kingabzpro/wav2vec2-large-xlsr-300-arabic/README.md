---
language: 
- ar

license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
metrics:
- wer
- cer
model-index:
- name: wav2vec2-xls-r-300m-arabic
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_7_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice ar # Required. Example: Common Voice zh-CN
      args: ar        # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 38.83  # Required. Example: 20.90
        name: Test WER With LM    # Optional. Example: Test WER
        
      - type: cer    # Required. Example: wer
        value: 15.33  # Required. Example: 20.90
        name: Test CER With LM   # Optional. Example: Test WER
        
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-300-arabic

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4514
- Wer: 0.4256
- Cer: 0.1528

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xlsr-300-arabic --dataset mozilla-foundation/common_voice_7_0 --config ur --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "kingabzpro/wav2vec2-large-xlsr-300-arabic"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "ar", split="test", streaming=True, use_auth_token=True))
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
- learning_rate: 0.0003
- train_batch_size: 64
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 5.4375        | 1.8   | 500  | 3.3330          | 1.0    | 1.0    |
| 2.2187        | 3.6   | 1000 | 0.7790          | 0.6501 | 0.2338 |
| 0.9471        | 5.4   | 1500 | 0.5353          | 0.5015 | 0.1822 |
| 0.7416        | 7.19  | 2000 | 0.4889          | 0.4490 | 0.1640 |
| 0.6358        | 8.99  | 2500 | 0.4514          | 0.4256 | 0.1528 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
