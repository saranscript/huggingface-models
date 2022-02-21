---
language:
- sv-SE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- sv
- robust-speech-event
- model_for_talk
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: XLS-R-300M - Swedish
  results:
  - task: 
      name: Automatic Speech Recognition 
      type: automatic-speech-recognition
    dataset:
      name: Common Voice 7
      type: mozilla-foundation/common_voice_7_0
      args: sv-SE
    metrics:
       - name: Test WER
         type: wer
         value: 16.98
       - name: Test CER
         type: cer
         value: 5.66
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
         value: 27.01
       - name: Test CER
         type: cer
         value: 13.14
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLS-R-300m-SV

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - SV-SE dataset.
It achieves the following results on the evaluation set:

- Loss: 0.3171
- Wer: 0.2468

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.3349        | 1.45  | 500   | 3.2858          | 1.0    |
| 2.9298        | 2.91  | 1000  | 2.9225          | 1.0000 |
| 2.0839        | 4.36  | 1500  | 1.1546          | 0.8295 |
| 1.7093        | 5.81  | 2000  | 0.6827          | 0.5701 |
| 1.5855        | 7.27  | 2500  | 0.5597          | 0.4947 |
| 1.4831        | 8.72  | 3000  | 0.4923          | 0.4527 |
| 1.4416        | 10.17 | 3500  | 0.4670          | 0.4270 |
| 1.3848        | 11.63 | 4000  | 0.4341          | 0.3980 |
| 1.3749        | 13.08 | 4500  | 0.4203          | 0.4011 |
| 1.3311        | 14.53 | 5000  | 0.4310          | 0.3961 |
| 1.317         | 15.99 | 5500  | 0.3898          | 0.4322 |
| 1.2799        | 17.44 | 6000  | 0.3806          | 0.3572 |
| 1.2771        | 18.89 | 6500  | 0.3828          | 0.3427 |
| 1.2451        | 20.35 | 7000  | 0.3702          | 0.3359 |
| 1.2182        | 21.8  | 7500  | 0.3685          | 0.3270 |
| 1.2152        | 23.26 | 8000  | 0.3650          | 0.3308 |
| 1.1837        | 24.71 | 8500  | 0.3568          | 0.3187 |
| 1.1721        | 26.16 | 9000  | 0.3659          | 0.3249 |
| 1.1764        | 27.61 | 9500  | 0.3547          | 0.3145 |
| 1.1606        | 29.07 | 10000 | 0.3514          | 0.3104 |
| 1.1431        | 30.52 | 10500 | 0.3469          | 0.3062 |
| 1.1047        | 31.97 | 11000 | 0.3313          | 0.2979 |
| 1.1315        | 33.43 | 11500 | 0.3298          | 0.2992 |
| 1.1022        | 34.88 | 12000 | 0.3296          | 0.2973 |
| 1.0935        | 36.34 | 12500 | 0.3278          | 0.2926 |
| 1.0676        | 37.79 | 13000 | 0.3208          | 0.2868 |
| 1.0571        | 39.24 | 13500 | 0.3322          | 0.2885 |
| 1.0536        | 40.7  | 14000 | 0.3245          | 0.2831 |
| 1.0525        | 42.15 | 14500 | 0.3285          | 0.2826 |
| 1.0464        | 43.6  | 15000 | 0.3223          | 0.2796 |
| 1.0415        | 45.06 | 15500 | 0.3166          | 0.2774 |
| 1.0356        | 46.51 | 16000 | 0.3177          | 0.2746 |
| 1.04          | 47.96 | 16500 | 0.3150          | 0.2735 |
| 1.0209        | 49.42 | 17000 | 0.3175          | 0.2731 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.10.3

#### Evaluation Commands

1. To evaluate on `mozilla-foundation/common_voice_7_0` with split `test`

```bash
python eval.py --model_id hf-test/xls-r-300m-sv --dataset mozilla-foundation/common_voice_7_0 --config sv-SE --split test
```

2. To evaluate on `speech-recognition-community-v2/dev_data`

```bash
python eval.py --model_id hf-test/xls-r-300m-sv --dataset speech-recognition-community-v2/dev_data --config sv --split validation --chunk_length_s 5.0 --stride_length_s 1.0
```

### Inference With LM

```python
import torch
from datasets import load_dataset
from transformers import AutoModelForCTC, AutoProcessor
import torchaudio.functional as F


model_id = "hf-test/xls-r-300m-sv"

sample_iter = iter(load_dataset("mozilla-foundation/common_voice_7_0", "sv-SE", split="test", streaming=True, use_auth_token=True))

sample = next(sample_iter)
resampled_audio = F.resample(torch.tensor(sample["audio"]["array"]), 48_000, 16_000).numpy()

model = AutoModelForCTC.from_pretrained(model_id)
processor = AutoProcessor.from_pretrained(model_id)

input_values = processor(resampled_audio, return_tensors="pt").input_values

with torch.no_grad():
    logits = model(input_values).logits

transcription = processor.batch_decode(logits.numpy()).text
# => "jag lämnade grovjobbet åt honom"
```

### Eval results on Common Voice 7 "test" (WER):

| Without LM | With LM (run `./eval.py`) |
|---|---|
| 24.68 | 16.98 |


