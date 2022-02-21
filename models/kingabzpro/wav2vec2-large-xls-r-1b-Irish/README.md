---
language: 
- ga-IE 

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
- name: wav2vec2-large-xls-r-1b-Irish-Abid
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice ga-IE  # Required. Example: Common Voice zh-CN
      args: ga-IE         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 38.45 # Required. Example: 20.90
        name: Test WER With LM   # Optional. Example: Test WER
        
      - type: cer    # Required. Example: wer
        value: 16.52  # Required. Example: 20.90
        name: Test CER With LM   # Optional. Example: Test WER
        
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-1b-Irish

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3599
- Wer: 0.4236
- Cer: 0.1768

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xls-r-1b-Irish --dataset mozilla-foundation/common_voice_8_0 --config ga-IE --split test
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "kingabzpro/wav2vec2-large-xls-r-1b-Irish"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "ga-IE", split="test", streaming=True, use_auth_token=True))
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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 200
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 6.3955        | 12.48 | 100  | 2.9897          | 1.0    | 1.0    |
| 2.3811        | 24.97 | 200  | 1.2304          | 0.7140 | 0.3106 |
| 1.0476        | 37.48 | 300  | 1.0661          | 0.5597 | 0.2407 |
| 0.7014        | 49.97 | 400  | 1.1788          | 0.4799 | 0.1947 |
| 0.4409        | 62.48 | 500  | 1.2649          | 0.4658 | 0.1997 |
| 0.4839        | 74.97 | 600  | 1.3259          | 0.4450 | 0.1868 |
| 0.3643        | 87.48 | 700  | 1.3506          | 0.4312 | 0.1760 |
| 0.3468        | 99.97 | 800  | 1.3599          | 0.4236 | 0.1768 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
