---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: unispeech-sat-base-timit-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# unispeech-sat-base-timit-ft

This model is a fine-tuned version of [microsoft/unispeech-sat-base](https://huggingface.co/microsoft/unispeech-sat-base) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6712
- Wer: 0.4101

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
| 3.2582        | 0.69  | 100  | 3.1651          | 1.0    |
| 2.9542        | 1.38  | 200  | 2.9567          | 1.0    |
| 2.9656        | 2.07  | 300  | 2.9195          | 1.0    |
| 2.8946        | 2.76  | 400  | 2.8641          | 1.0    |
| 1.9305        | 3.45  | 500  | 1.7680          | 1.0029 |
| 1.0134        | 4.14  | 600  | 1.0184          | 0.6942 |
| 0.8355        | 4.83  | 700  | 0.7769          | 0.6080 |
| 0.8724        | 5.52  | 800  | 0.7182          | 0.6035 |
| 0.5619        | 6.21  | 900  | 0.6823          | 0.5406 |
| 0.4247        | 6.9   | 1000 | 0.6279          | 0.5237 |
| 0.4257        | 7.59  | 1100 | 0.6056          | 0.5000 |
| 0.5007        | 8.28  | 1200 | 0.5870          | 0.4918 |
| 0.3854        | 8.97  | 1300 | 0.6200          | 0.4804 |
| 0.264         | 9.66  | 1400 | 0.6030          | 0.4600 |
| 0.1989        | 10.34 | 1500 | 0.6049          | 0.4588 |
| 0.3196        | 11.03 | 1600 | 0.5946          | 0.4599 |
| 0.2622        | 11.72 | 1700 | 0.6282          | 0.4422 |
| 0.1697        | 12.41 | 1800 | 0.6559          | 0.4413 |
| 0.1464        | 13.1  | 1900 | 0.6349          | 0.4328 |
| 0.2277        | 13.79 | 2000 | 0.6133          | 0.4284 |
| 0.221         | 14.48 | 2100 | 0.6617          | 0.4219 |
| 0.1391        | 15.17 | 2200 | 0.6705          | 0.4235 |
| 0.112         | 15.86 | 2300 | 0.6207          | 0.4218 |
| 0.1717        | 16.55 | 2400 | 0.6749          | 0.4184 |
| 0.2081        | 17.24 | 2500 | 0.6756          | 0.4169 |
| 0.1244        | 17.93 | 2600 | 0.6750          | 0.4181 |
| 0.0978        | 18.62 | 2700 | 0.6500          | 0.4115 |
| 0.128         | 19.31 | 2800 | 0.6750          | 0.4106 |
| 0.1791        | 20.0  | 2900 | 0.6712          | 0.4101 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
