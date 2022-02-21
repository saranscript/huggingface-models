---
language: 
- pa-IN

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
- name: wav2vec2-punjabi-V8-Abid
  results:
  - task: 
      type: automatic-speech-recognition  # Required. Example: automatic-speech-recognition
      name: Speech Recognition  # Optional. Example: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0  # Required. Example: common_voice. Use dataset id from https://hf.co/datasets
      name: Common Voice pa-IN  # Required. Example: Common Voice zh-CN
      args: pa-IN         # Optional. Example: zh-CN
    metrics:
      - type: wer    # Required. Example: wer
        value: 36.02 # Required. Example: 20.90
        name: Test WER With LM    # Optional. Example: Test WER
      - type: cer    # Required. Example: wer
        value: 12.81   # Required. Example: 20.90
        name: Test CER With LM  # Optional. Example: Test WER

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xlsr-53-punjabi

This model is a fine-tuned version of [Harveenchadha/vakyansh-wav2vec2-punjabi-pam-10](https://huggingface.co/Harveenchadha/vakyansh-wav2vec2-punjabi-pam-10) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2101
- Wer: 0.4939
- Cer: 0.2238

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id kingabzpro/wav2vec2-large-xlsr-53-punjabi --dataset mozilla-foundation/common_voice_8_0 --config pa-IN --split test
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "kingabzpro/wav2vec2-large-xlsr-53-punjabi"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "pa-IN", split="test", streaming=True, use_auth_token=True))
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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 200
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|
| 11.0563       | 3.7   | 100  | 1.9492          | 0.7123 | 0.3872 |
| 1.6715        | 7.41  | 200  | 1.3142          | 0.6433 | 0.3086 |
| 0.9117        | 11.11 | 300  | 1.2733          | 0.5657 | 0.2627 |
| 0.666         | 14.81 | 400  | 1.2730          | 0.5598 | 0.2534 |
| 0.4225        | 18.52 | 500  | 1.2548          | 0.5300 | 0.2399 |
| 0.3209        | 22.22 | 600  | 1.2166          | 0.5229 | 0.2372 |
| 0.2678        | 25.93 | 700  | 1.1795          | 0.5041 | 0.2276 |
| 0.2088        | 29.63 | 800  | 1.2101          | 0.4939 | 0.2238 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
