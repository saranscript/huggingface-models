---
language: 
- as
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
metrics:
- wer
model-index:
- name: wav2vec2-large-xls-r-300m-as
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_7_0
      name: Common Voice 7
      args: as
    metrics:
      - type: wer    # Required. Example: wer
        value: 56.995  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 20.390
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-as

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9068
- Wer: 0.6679

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

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
- lr_scheduler_warmup_ratio: 0.12
- num_epochs: 240

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 5.7027        | 21.05  | 400  | 3.4157          | 1.0    |
| 1.1638        | 42.1   | 800  | 1.3498          | 0.7461 |
| 0.2266        | 63.15  | 1200 | 1.6147          | 0.7273 |
| 0.1473        | 84.21  | 1600 | 1.6649          | 0.7108 |
| 0.1043        | 105.26 | 2000 | 1.7691          | 0.7090 |
| 0.0779        | 126.31 | 2400 | 1.8300          | 0.7009 |
| 0.0613        | 147.36 | 2800 | 1.8681          | 0.6916 |
| 0.0471        | 168.41 | 3200 | 1.8567          | 0.6875 |
| 0.0343        | 189.46 | 3600 | 1.9054          | 0.6840 |
| 0.0265        | 210.51 | 4000 | 1.9020          | 0.6786 |
| 0.0219        | 231.56 | 4400 | 1.9068          | 0.6679 |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-large-xls-r-300m-as --dataset mozilla-foundation/common_voice_7_0 --config as --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-large-xls-r-300m-as"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_7_0", "as", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "জাহাজত তো তিশকুৰলৈ যাব কিন্তু জহাজিটো আহিপনে"
```

### Eval results on Common Voice 7 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 67 | 56.995 |

