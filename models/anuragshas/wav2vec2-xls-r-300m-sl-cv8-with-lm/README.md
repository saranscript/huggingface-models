---
language:
- sl
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Slovenian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: sl
    metrics:
       - name: Test WER
         type: wer
         value: 12.736
       - name: Test CER
         type: cer
         value: 3.605
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: sl
    metrics:
       - name: Test WER
         type: wer
         value: 45.587
       - name: Test CER
         type: cer
         value: 20.886
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Slovenian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SL dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2578
- Wer: 0.2273

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
| 3.1829        | 4.88  | 400  | 3.1228          | 1.0    |
| 2.8675        | 9.76  | 800  | 2.8616          | 0.9993 |
| 1.583         | 14.63 | 1200 | 0.6392          | 0.6239 |
| 1.1959        | 19.51 | 1600 | 0.3602          | 0.3651 |
| 1.0276        | 24.39 | 2000 | 0.3021          | 0.2981 |
| 0.9671        | 29.27 | 2400 | 0.2872          | 0.2739 |
| 0.873         | 34.15 | 2800 | 0.2593          | 0.2459 |
| 0.8513        | 39.02 | 3200 | 0.2617          | 0.2473 |
| 0.8132        | 43.9  | 3600 | 0.2548          | 0.2426 |
| 0.7935        | 48.78 | 4000 | 0.2637          | 0.2353 |
| 0.7565        | 53.66 | 4400 | 0.2629          | 0.2322 |
| 0.7359        | 58.54 | 4800 | 0.2579          | 0.2253 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-sl-cv8-with-lm --dataset mozilla-foundation/common_voice_8_0 --config sl --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-sl-cv8-with-lm --dataset speech-recognition-community-v2/dev_data --config sl --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-xls-r-300m-sl-cv8-with-lm"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "sl", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "zmago je divje od letel s helikopterjem visoko vzrak"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 19.938 | 12.736 |