---
language: 
- ur
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
metrics:
- wer
model-index:
- name: wav2vec2-large-xls-r-300m-ur-cv8
  results:
  - task: 
      type: automatic-speech-recognition
      name: Speech Recognition
    dataset:
      type: mozilla-foundation/common_voice_8_0
      name: Common Voice 8
      args: ur
    metrics:
      - type: wer    # Required. Example: wer
        value: 42.376  # Required. Example: 20.90
        name: Test WER    # Optional. Example: Test WER
      - name: Test CER
        type: cer
        value: 18.180
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-ur-cv8

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1443
- Wer: 0.5677

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
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 200

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 3.6269        | 15.98  | 400  | 3.3246          | 1.0    |
| 3.0546        | 31.98  | 800  | 2.8148          | 0.9963 |
| 1.4589        | 47.98  | 1200 | 1.0237          | 0.6584 |
| 1.0911        | 63.98  | 1600 | 0.9524          | 0.5966 |
| 0.8879        | 79.98  | 2000 | 0.9827          | 0.5822 |
| 0.7467        | 95.98  | 2400 | 0.9923          | 0.5840 |
| 0.6427        | 111.98 | 2800 | 0.9988          | 0.5714 |
| 0.5685        | 127.98 | 3200 | 1.0872          | 0.5807 |
| 0.5068        | 143.98 | 3600 | 1.1194          | 0.5822 |
| 0.463         | 159.98 | 4000 | 1.1138          | 0.5692 |
| 0.4212        | 175.98 | 4400 | 1.1232          | 0.5714 |
| 0.4056        | 191.98 | 4800 | 1.1443          | 0.5677 |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-large-xls-r-300m-ur-cv8 --dataset mozilla-foundation/common_voice_8_0 --config ur --split test
```


### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-large-xls-r-300m-ur-cv8"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "ur", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "اب نے ٹ پیس ان لیتے ہیں"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 52.146 | 42.376 |