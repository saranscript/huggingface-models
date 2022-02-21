---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: wav2vec2-random
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-random

This model is a fine-tuned version of [patrickvonplaten/wav2vec2-base-random](https://huggingface.co/patrickvonplaten/wav2vec2-base-random) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 3.1593
- Wer: 0.8364

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
- train_batch_size: 32
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.9043        | 0.69  | 100  | 2.9683          | 1.0    |
| 2.8537        | 1.38  | 200  | 2.9281          | 0.9997 |
| 2.7803        | 2.07  | 300  | 2.7330          | 0.9999 |
| 2.6806        | 2.76  | 400  | 2.5792          | 1.0    |
| 2.4136        | 3.45  | 500  | 2.4327          | 0.9948 |
| 2.1682        | 4.14  | 600  | 2.3508          | 0.9877 |
| 2.2577        | 4.83  | 700  | 2.2176          | 0.9773 |
| 2.355         | 5.52  | 800  | 2.1753          | 0.9542 |
| 1.8588        | 6.21  | 900  | 2.0650          | 0.8851 |
| 1.6831        | 6.9   | 1000 | 2.0109          | 0.8618 |
| 1.888         | 7.59  | 1100 | 1.9660          | 0.8418 |
| 2.0066        | 8.28  | 1200 | 1.9847          | 0.8531 |
| 1.7044        | 8.97  | 1300 | 1.9760          | 0.8527 |
| 1.3168        | 9.66  | 1400 | 2.0708          | 0.8327 |
| 1.2143        | 10.34 | 1500 | 2.0601          | 0.8419 |
| 1.6189        | 11.03 | 1600 | 2.0960          | 0.8299 |
| 1.13          | 11.72 | 1700 | 2.2540          | 0.8408 |
| 0.8001        | 12.41 | 1800 | 2.4260          | 0.8306 |
| 0.7769        | 13.1  | 1900 | 2.4182          | 0.8445 |
| 1.2165        | 13.79 | 2000 | 2.3666          | 0.8284 |
| 0.8026        | 14.48 | 2100 | 2.7118          | 0.8662 |
| 0.5148        | 15.17 | 2200 | 2.7957          | 0.8526 |
| 0.4921        | 15.86 | 2300 | 2.8244          | 0.8346 |
| 0.7629        | 16.55 | 2400 | 2.8944          | 0.8370 |
| 0.5762        | 17.24 | 2500 | 3.0335          | 0.8367 |
| 0.4076        | 17.93 | 2600 | 3.0776          | 0.8358 |
| 0.3395        | 18.62 | 2700 | 3.1572          | 0.8261 |
| 0.4862        | 19.31 | 2800 | 3.1319          | 0.8414 |
| 0.5061        | 20.0  | 2900 | 3.1593          | 0.8364 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
