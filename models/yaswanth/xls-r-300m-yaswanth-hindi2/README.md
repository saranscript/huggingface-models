---
language:
- hi
license: apache-2.0
tags:
- generated_from_trainer
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: xls-r-300m-yaswanth-hindi2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xls-r-300m-yaswanth-hindi2

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7163
- Wer: 0.6951

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0007
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 4.986         | 4.46  | 500   | 2.0194          | 1.1857 |
| 0.9232        | 8.93  | 1000  | 1.2665          | 0.8435 |
| 0.5094        | 13.39 | 1500  | 1.2473          | 0.7893 |
| 0.3618        | 17.86 | 2000  | 1.3675          | 0.7789 |
| 0.2914        | 22.32 | 2500  | 1.3725          | 0.7914 |
| 0.2462        | 26.79 | 3000  | 1.4567          | 0.7795 |
| 0.228         | 31.25 | 3500  | 1.6179          | 0.7872 |
| 0.1995        | 35.71 | 4000  | 1.4932          | 0.7555 |
| 0.1878        | 40.18 | 4500  | 1.5352          | 0.7480 |
| 0.165         | 44.64 | 5000  | 1.5238          | 0.7440 |
| 0.1514        | 49.11 | 5500  | 1.5842          | 0.7498 |
| 0.1416        | 53.57 | 6000  | 1.6662          | 0.7524 |
| 0.1351        | 58.04 | 6500  | 1.6280          | 0.7356 |
| 0.1196        | 62.5  | 7000  | 1.6329          | 0.7250 |
| 0.1109        | 66.96 | 7500  | 1.6435          | 0.7302 |
| 0.1008        | 71.43 | 8000  | 1.7058          | 0.7170 |
| 0.0907        | 75.89 | 8500  | 1.6880          | 0.7387 |
| 0.0816        | 80.36 | 9000  | 1.6957          | 0.7031 |
| 0.0743        | 84.82 | 9500  | 1.7547          | 0.7222 |
| 0.0694        | 89.29 | 10000 | 1.6974          | 0.7117 |
| 0.0612        | 93.75 | 10500 | 1.7251          | 0.7020 |
| 0.0577        | 98.21 | 11000 | 1.7163          | 0.6951 |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
