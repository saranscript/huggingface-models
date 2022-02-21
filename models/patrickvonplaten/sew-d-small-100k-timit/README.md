---
license: apache-2.0
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: sew-d-small-100k-timit
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sew-d-small-100k-timit

This model is a fine-tuned version of [asapp/sew-d-small-100k](https://huggingface.co/asapp/sew-d-small-100k) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7541
- Wer: 0.8061

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
| 4.2068        | 0.69  | 100  | 4.0802          | 1.0    |
| 2.9805        | 1.38  | 200  | 2.9792          | 1.0    |
| 2.9781        | 2.07  | 300  | 2.9408          | 1.0    |
| 2.9655        | 2.76  | 400  | 2.9143          | 1.0    |
| 2.8953        | 3.45  | 500  | 2.8775          | 1.0    |
| 2.7718        | 4.14  | 600  | 2.7787          | 1.0    |
| 2.6711        | 4.83  | 700  | 2.6401          | 0.9786 |
| 2.6403        | 5.52  | 800  | 2.5435          | 1.0392 |
| 2.4052        | 6.21  | 900  | 2.4580          | 1.0706 |
| 2.1708        | 6.9   | 1000 | 2.2800          | 1.0090 |
| 2.2555        | 7.59  | 1100 | 2.1493          | 0.9579 |
| 2.3673        | 8.28  | 1200 | 2.0709          | 0.9051 |
| 2.091         | 8.97  | 1300 | 2.0258          | 0.8926 |
| 1.8433        | 9.66  | 1400 | 1.9645          | 0.8243 |
| 1.6824        | 10.34 | 1500 | 1.9211          | 0.8707 |
| 2.2282        | 11.03 | 1600 | 1.8914          | 0.8695 |
| 1.9027        | 11.72 | 1700 | 1.8718          | 0.8343 |
| 1.6303        | 12.41 | 1800 | 1.8646          | 0.8232 |
| 1.648         | 13.1  | 1900 | 1.8297          | 0.8177 |
| 2.0429        | 13.79 | 2000 | 1.8127          | 0.8642 |
| 1.8833        | 14.48 | 2100 | 1.8005          | 0.8307 |
| 1.5996        | 15.17 | 2200 | 1.7926          | 0.8467 |
| 1.4876        | 15.86 | 2300 | 1.7795          | 0.8341 |
| 1.8925        | 16.55 | 2400 | 1.7716          | 0.8199 |
| 1.814         | 17.24 | 2500 | 1.7846          | 0.8086 |
| 1.536         | 17.93 | 2600 | 1.7655          | 0.8019 |
| 1.4476        | 18.62 | 2700 | 1.7599          | 0.8070 |
| 1.7629        | 19.31 | 2800 | 1.7589          | 0.8119 |
| 1.7646        | 20.0  | 2900 | 1.7541          | 0.8061 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
