---
language:
- fa
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: common7
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# common7

This model is a fine-tuned version of [common7/checkpoint-18500](https://huggingface.co/common7/checkpoint-18500) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - FA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3448
- Wer: 0.3478

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 6e-05
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 150.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step  | Validation Loss | Wer    |
|:-------------:|:------:|:-----:|:---------------:|:------:|
| 2.957         | 3.29   | 500   | 2.9503          | 1.0    |
| 1.7225        | 6.58   | 1000  | 0.8860          | 0.7703 |
| 1.4907        | 9.86   | 1500  | 0.6555          | 0.6673 |
| 1.4177        | 13.16  | 2000  | 0.5784          | 0.6076 |
| 1.3425        | 16.45  | 2500  | 0.5379          | 0.5718 |
| 1.33          | 19.73  | 3000  | 0.4962          | 0.5245 |
| 1.4378        | 23.03  | 3500  | 0.4699          | 0.5098 |
| 1.1894        | 26.31  | 4000  | 0.4527          | 0.4848 |
| 1.1844        | 29.6   | 4500  | 0.4309          | 0.4651 |
| 1.1795        | 32.89  | 5000  | 0.4131          | 0.4524 |
| 1.1471        | 36.18  | 5500  | 0.4052          | 0.4435 |
| 1.1337        | 39.47  | 6000  | 0.3927          | 0.4363 |
| 1.1896        | 42.76  | 6500  | 0.3811          | 0.4254 |
| 1.1847        | 46.05  | 7000  | 0.3855          | 0.4129 |
| 0.9954        | 49.34  | 7500  | 0.3729          | 0.3981 |
| 1.0293        | 52.63  | 8000  | 0.3637          | 0.4014 |
| 1.0224        | 55.92  | 8500  | 0.3578          | 0.3885 |
| 1.012         | 59.21  | 9000  | 0.3629          | 0.3930 |
| 1.0772        | 62.5   | 9500  | 0.3635          | 0.3906 |
| 1.0344        | 65.79  | 10000 | 0.3469          | 0.3771 |
| 0.9457        | 69.08  | 10500 | 0.3435          | 0.3735 |
| 0.9307        | 72.37  | 11000 | 0.3519          | 0.3762 |
| 0.9523        | 75.65  | 11500 | 0.3443          | 0.3666 |
| 0.9523        | 78.94  | 12000 | 0.3502          | 0.3757 |
| 0.9475        | 82.24  | 12500 | 0.3509          | 0.3643 |
| 0.9971        | 85.52  | 13000 | 0.3502          | 0.3626 |
| 0.9058        | 88.81  | 13500 | 0.3472          | 0.3605 |
| 0.8922        | 92.1   | 14000 | 0.3530          | 0.3618 |
| 0.9           | 95.39  | 14500 | 0.3500          | 0.3574 |
| 0.9051        | 98.68  | 15000 | 0.3456          | 0.3535 |
| 0.9304        | 101.97 | 15500 | 0.3438          | 0.3578 |
| 0.9433        | 105.26 | 16000 | 0.3396          | 0.3530 |
| 0.8988        | 108.55 | 16500 | 0.3436          | 0.3539 |
| 0.8789        | 111.84 | 17000 | 0.3426          | 0.3516 |
| 0.8667        | 115.13 | 17500 | 0.3438          | 0.3506 |
| 0.8895        | 118.42 | 18000 | 0.3434          | 0.3503 |
| 0.8888        | 121.71 | 18500 | 0.3425          | 0.3494 |
| 0.9453        | 125.0  | 19000 | 0.3415          | 0.3480 |
| 0.9267        | 128.29 | 19500 | 0.3477          | 0.3503 |
| 0.8315        | 131.58 | 20000 | 0.3476          | 0.3505 |
| 0.8542        | 134.86 | 20500 | 0.3475          | 0.3506 |
| 0.8478        | 138.16 | 21000 | 0.3430          | 0.3481 |
| 0.8643        | 141.45 | 21500 | 0.3451          | 0.3485 |
| 0.8705        | 144.73 | 22000 | 0.3444          | 0.3474 |
| 0.9869        | 148.03 | 22500 | 0.3441          | 0.3493 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2
- Datasets 1.18.3.dev0
- Tokenizers 0.10.3
