---
language:
- lv
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: XLS-R-300M - Latvian
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 8
      type: mozilla-foundation/common_voice_8_0
      args: lv
    metrics:
       - name: Test WER
         type: wer
         value: 9.633
       - name: Test CER
         type: cer
         value: 2.614
  - task: 
      name: Automatic Speech Recognition
      type: automatic-speech-recognition
    dataset:
      name: Robust Speech Event - Dev Data
      type: speech-recognition-community-v2/dev_data
      args: lv
    metrics:
       - name: Test WER
         type: wer
         value: 36.110
       - name: Test CER
         type: cer
         value: 14.244
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300M - Latvian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - LV dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1660
- Wer: 0.1705

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
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.489         | 2.56  | 400  | 3.3590          | 1.0    |
| 2.9903        | 5.13  | 800  | 2.9704          | 1.0001 |
| 1.6712        | 7.69  | 1200 | 0.6179          | 0.6566 |
| 1.2635        | 10.26 | 1600 | 0.3176          | 0.4531 |
| 1.0819        | 12.82 | 2000 | 0.2517          | 0.3508 |
| 1.0136        | 15.38 | 2400 | 0.2257          | 0.3124 |
| 0.9625        | 17.95 | 2800 | 0.1975          | 0.2311 |
| 0.901         | 20.51 | 3200 | 0.1986          | 0.2097 |
| 0.8842        | 23.08 | 3600 | 0.1904          | 0.2039 |
| 0.8542        | 25.64 | 4000 | 0.1847          | 0.1981 |
| 0.8244        | 28.21 | 4400 | 0.1805          | 0.1847 |
| 0.7689        | 30.77 | 4800 | 0.1736          | 0.1832 |
| 0.7825        | 33.33 | 5200 | 0.1698          | 0.1821 |
| 0.7817        | 35.9  | 5600 | 0.1758          | 0.1803 |
| 0.7488        | 38.46 | 6000 | 0.1663          | 0.1760 |
| 0.7171        | 41.03 | 6400 | 0.1636          | 0.1721 |
| 0.7222        | 43.59 | 6800 | 0.1663          | 0.1729 |
| 0.7156        | 46.15 | 7200 | 0.1633          | 0.1715 |
| 0.7121        | 48.72 | 7600 | 0.1666          | 0.1718 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0

#### Evaluation Commands
1. To evaluate on `mozilla-foundation/common_voice_8_0` with split `test`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-lv-cv8-with-lm --dataset mozilla-foundation/common_voice_8_0 --config lv --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id anuragshas/wav2vec2-xls-r-300m-lv-cv8-with-lm --dataset speech-recognition-community-v2/dev_data --config lv --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F
model_id = "anuragshas/wav2vec2-xls-r-300m-lv-cv8-with-lm"
sample_iter = iter(load_dataset("mozilla-foundation/common_voice_8_0", "lv", split="test", streaming=True, use_auth_token=True))
sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()
model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)
input_values = processor(resampled_audio, return_tensors="pt").input_values
with torch.no_grad():
    logits = model(input_values).logits
transcription = processor.batch_decode(logits.numpy()).text
# => "domāju ka viņam viss labi"
```

### Eval results on Common Voice 8 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 16.997 | 9.633 |
