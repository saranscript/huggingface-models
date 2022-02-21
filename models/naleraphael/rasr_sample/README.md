---
language:
- sv-SE
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: rasr_sample
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# rasr_sample

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - SV-SE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3147
- Wer: 0.2676

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
| 3.3332        | 1.45  | 500   | 3.3031          | 1.0    |
| 2.9272        | 2.91  | 1000  | 2.9353          | 0.9970 |
| 2.0736        | 4.36  | 1500  | 1.1565          | 0.8714 |
| 1.7339        | 5.81  | 2000  | 0.7156          | 0.6688 |
| 1.5989        | 7.27  | 2500  | 0.5791          | 0.5519 |
| 1.4916        | 8.72  | 3000  | 0.5038          | 0.5169 |
| 1.4562        | 10.17 | 3500  | 0.4861          | 0.4805 |
| 1.3893        | 11.63 | 4000  | 0.4584          | 0.4761 |
| 1.3797        | 13.08 | 4500  | 0.4298          | 0.4686 |
| 1.3508        | 14.53 | 5000  | 0.4138          | 0.3744 |
| 1.3165        | 15.99 | 5500  | 0.4015          | 0.3578 |
| 1.281         | 17.44 | 6000  | 0.3883          | 0.3472 |
| 1.2682        | 18.89 | 6500  | 0.3904          | 0.3434 |
| 1.2477        | 20.35 | 7000  | 0.3726          | 0.3321 |
| 1.2364        | 21.8  | 7500  | 0.3685          | 0.3281 |
| 1.2041        | 23.26 | 8000  | 0.3597          | 0.3194 |
| 1.1901        | 24.71 | 8500  | 0.3542          | 0.3203 |
| 1.1903        | 26.16 | 9000  | 0.3500          | 0.3138 |
| 1.1677        | 27.61 | 9500  | 0.3458          | 0.3067 |
| 1.1718        | 29.07 | 10000 | 0.3595          | 0.3112 |
| 1.1562        | 30.52 | 10500 | 0.3433          | 0.3022 |
| 1.1392        | 31.97 | 11000 | 0.3440          | 0.2936 |
| 1.1258        | 33.43 | 11500 | 0.3396          | 0.2950 |
| 1.1067        | 34.88 | 12000 | 0.3379          | 0.2939 |
| 1.0953        | 36.34 | 12500 | 0.3370          | 0.2868 |
| 1.0835        | 37.79 | 13000 | 0.3317          | 0.2860 |
| 1.0772        | 39.24 | 13500 | 0.3302          | 0.2854 |
| 1.0853        | 40.7  | 14000 | 0.3265          | 0.2783 |
| 1.0689        | 42.15 | 14500 | 0.3306          | 0.2770 |
| 1.0394        | 43.6  | 15000 | 0.3233          | 0.2757 |
| 1.0581        | 45.06 | 15500 | 0.3199          | 0.2713 |
| 1.0362        | 46.51 | 16000 | 0.3154          | 0.2683 |
| 1.0406        | 47.96 | 16500 | 0.3176          | 0.2688 |
| 1.0082        | 49.42 | 17000 | 0.3149          | 0.2679 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
