---
tags:
- automatic-speech-recognition
- timit_asr
- generated_from_trainer
datasets:
- timit_asr
model-index:
- name: unispeech-sat-large-timit-ft
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# unispeech-sat-large-timit-ft

This model is a fine-tuned version of [microsoft/unispeech-sat-large](https://huggingface.co/microsoft/unispeech-sat-large) on the TIMIT_ASR - NA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6074
- Wer: 0.3880

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
| 6.2516        | 0.69  | 100  | 5.8638          | 1.0    |
| 2.9596        | 1.38  | 200  | 2.9550          | 1.0    |
| 2.8831        | 2.07  | 300  | 2.8547          | 1.0    |
| 2.3223        | 2.76  | 400  | 2.2044          | 1.0063 |
| 1.2104        | 3.45  | 500  | 1.0845          | 0.7706 |
| 0.6779        | 4.14  | 600  | 0.7342          | 0.5663 |
| 0.6319        | 4.83  | 700  | 0.6054          | 0.4881 |
| 0.664         | 5.52  | 800  | 0.5808          | 0.4913 |
| 0.402         | 6.21  | 900  | 0.5647          | 0.4611 |
| 0.3176        | 6.9   | 1000 | 0.5211          | 0.4440 |
| 0.3392        | 7.59  | 1100 | 0.5187          | 0.4359 |
| 0.3888        | 8.28  | 1200 | 0.5501          | 0.4391 |
| 0.2874        | 8.97  | 1300 | 0.5249          | 0.4148 |
| 0.208         | 9.66  | 1400 | 0.5407          | 0.4152 |
| 0.1457        | 10.34 | 1500 | 0.5722          | 0.4155 |
| 0.2375        | 11.03 | 1600 | 0.5780          | 0.4059 |
| 0.2111        | 11.72 | 1700 | 0.5823          | 0.4094 |
| 0.1422        | 12.41 | 1800 | 0.5754          | 0.3977 |
| 0.125         | 13.1  | 1900 | 0.5784          | 0.4031 |
| 0.1996        | 13.79 | 2000 | 0.5630          | 0.3956 |
| 0.1747        | 14.48 | 2100 | 0.5880          | 0.3964 |
| 0.1263        | 15.17 | 2200 | 0.5987          | 0.3951 |
| 0.11          | 15.86 | 2300 | 0.5688          | 0.3964 |
| 0.1411        | 16.55 | 2400 | 0.6223          | 0.3906 |
| 0.1647        | 17.24 | 2500 | 0.6135          | 0.3960 |
| 0.1162        | 17.93 | 2600 | 0.6224          | 0.3960 |
| 0.098         | 18.62 | 2700 | 0.6017          | 0.3907 |
| 0.1183        | 19.31 | 2800 | 0.6121          | 0.3885 |
| 0.1717        | 20.0  | 2900 | 0.6074          | 0.3880 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.1
- Datasets 1.14.1.dev0
- Tokenizers 0.10.3
