---
language:
- he
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
- he
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-1b-hebrew
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-1b-hebrew

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3533
- Wer: 0.2251

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
- train_batch_size: 6
- eval_batch_size: 6
- seed: 42
- distributed_type: multi-GPU
- gradient_accumulation_steps: 4
- total_train_batch_size: 24
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 400
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.3587        | 0.47  | 400   | 1.1883          | 0.8392 |
| 1.8377        | 0.95  | 800   | 0.8831          | 0.6852 |
| 1.7118        | 1.42  | 1200  | 0.8031          | 0.6566 |
| 1.6741        | 1.89  | 1600  | 0.7518          | 0.6104 |
| 1.6163        | 2.36  | 2000  | 0.6888          | 0.5591 |
| 1.5782        | 2.84  | 2400  | 0.6580          | 0.5165 |
| 1.5548        | 3.31  | 2800  | 0.6506          | 0.5184 |
| 1.5249        | 3.78  | 3200  | 0.6198          | 0.5028 |
| 1.5078        | 4.26  | 3600  | 0.5992          | 0.4932 |
| 1.4836        | 4.73  | 4000  | 0.5705          | 0.4651 |
| 1.4505        | 5.2   | 4400  | 0.5489          | 0.4508 |
| 1.4481        | 5.67  | 4800  | 0.5577          | 0.4562 |
| 1.4136        | 6.15  | 5200  | 0.5452          | 0.4371 |
| 1.3861        | 6.62  | 5600  | 0.5101          | 0.4087 |
| 1.3772        | 7.09  | 6000  | 0.4933          | 0.3951 |
| 1.3478        | 7.56  | 6400  | 0.4849          | 0.3922 |
| 1.3394        | 8.04  | 6800  | 0.4805          | 0.3892 |
| 1.3095        | 8.51  | 7200  | 0.4839          | 0.3834 |
| 1.306         | 8.98  | 7600  | 0.4611          | 0.3587 |
| 1.2707        | 9.46  | 8000  | 0.4545          | 0.3730 |
| 1.2626        | 9.93  | 8400  | 0.4516          | 0.3524 |
| 1.2412        | 10.4  | 8800  | 0.4314          | 0.3310 |
| 1.2456        | 10.87 | 9200  | 0.4401          | 0.3459 |
| 1.2081        | 11.35 | 9600  | 0.4399          | 0.3356 |
| 1.1998        | 11.82 | 10000 | 0.4195          | 0.3215 |
| 1.1826        | 12.29 | 10400 | 0.4221          | 0.3178 |
| 1.1573        | 12.77 | 10800 | 0.4098          | 0.3084 |
| 1.1416        | 13.24 | 11200 | 0.4086          | 0.3119 |
| 1.1174        | 13.71 | 11600 | 0.3854          | 0.2910 |
| 1.1048        | 14.18 | 12000 | 0.3859          | 0.2824 |
| 1.0748        | 14.66 | 12400 | 0.3854          | 0.2757 |
| 1.0697        | 15.13 | 12800 | 0.3740          | 0.2724 |
| 1.0477        | 15.6  | 13200 | 0.3693          | 0.2643 |
| 1.0356        | 16.08 | 13600 | 0.3727          | 0.2561 |
| 1.0083        | 16.55 | 14000 | 0.3652          | 0.2501 |
| 1.0           | 17.02 | 14400 | 0.3641          | 0.2457 |
| 0.9779        | 17.49 | 14800 | 0.3568          | 0.2409 |
| 0.9596        | 17.97 | 15200 | 0.3558          | 0.2376 |
| 0.946         | 18.44 | 15600 | 0.3591          | 0.2311 |
| 0.9389        | 18.91 | 16000 | 0.3540          | 0.2283 |
| 0.9173        | 19.39 | 16400 | 0.3552          | 0.2265 |
| 0.9122        | 19.86 | 16800 | 0.3535          | 0.2250 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
