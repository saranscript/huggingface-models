---
tags:
- generated_from_trainer
datasets:
- librispeech_asr
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model was trained from scratch on the librispeech_asr dataset.
It achieves the following results on the evaluation set:
- Loss: 12.2365
- Wer: 1.0

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer |
|:-------------:|:-----:|:----:|:---------------:|:---:|
| 6.5774        | 0.28  | 500  | 10.5449         | 1.0 |
| 6.706         | 0.56  | 1000 | 9.4411          | 1.0 |
| 6.9182        | 0.84  | 1500 | 10.9554         | 1.0 |
| 6.7416        | 1.12  | 2000 | 10.0801         | 1.0 |
| 6.8778        | 1.4   | 2500 | 9.8569          | 1.0 |
| 6.7694        | 1.68  | 3000 | 10.4234         | 1.0 |
| 6.7415        | 1.96  | 3500 | 10.6545         | 1.0 |
| 6.5997        | 2.24  | 4000 | 10.4268         | 1.0 |
| 6.7672        | 2.52  | 4500 | 11.1929         | 1.0 |
| 6.5254        | 2.8   | 5000 | 12.2365         | 1.0 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
