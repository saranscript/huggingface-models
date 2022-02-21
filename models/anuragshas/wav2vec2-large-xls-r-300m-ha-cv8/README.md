---
language:
- ha
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
model-index:
- name: XLS-R-300M - Hausa
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice 8
      args: ha
    metrics:
      - type: wer    # Required. Example: wer
        value: 36.295  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 11.073
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Hausa

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6094
- Wer: 0.5234

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 8
- seed: 13
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine_with_restarts
- lr_scheduler_warmup_steps: 1000
- num_epochs: 100

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9599        | 6.56  | 400  | 2.8650          | 1.0    |
| 2.7357        | 13.11 | 800  | 2.7377          | 0.9951 |
| 1.3012        | 19.67 | 1200 | 0.6686          | 0.7111 |
| 1.0454        | 26.23 | 1600 | 0.5686          | 0.6137 |
| 0.9069        | 32.79 | 2000 | 0.5576          | 0.5815 |
| 0.82          | 39.34 | 2400 | 0.5502          | 0.5591 |
| 0.7413        | 45.9  | 2800 | 0.5970          | 0.5586 |
| 0.6872        | 52.46 | 3200 | 0.5817          | 0.5428 |
| 0.634         | 59.02 | 3600 | 0.5636          | 0.5314 |
| 0.6022        | 65.57 | 4000 | 0.5780          | 0.5229 |
| 0.5705        | 72.13 | 4400 | 0.6036          | 0.5323 |
| 0.5408        | 78.69 | 4800 | 0.6119          | 0.5336 |
| 0.5225        | 85.25 | 5200 | 0.6105          | 0.5270 |
| 0.5265        | 91.8  | 5600 | 0.6034          | 0.5231 |
| 0.5154        | 98.36 | 6000 | 0.6094          | 0.5234 |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-large-xls-r-300m-ha-cv8 --dataset mozilla-foundation/common_voice_8_0 --config ha --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-large-xls-r-300m-ha-cv8"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "ha", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "kakin hade ya ke da kyautar"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 47.821 | 36.295 |