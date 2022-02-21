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
- Loss: 6.9670
- Wer: 1.9878

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

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 6.7599        | 0.28  | 500  | 6.8755          | 1.2551 |
| 6.5943        | 0.56  | 1000 | 6.7702          | 1.5878 |
| 6.3146        | 0.84  | 1500 | 6.6981          | 1.6627 |
| 6.6112        | 1.12  | 2000 | 6.6760          | 1.9853 |
| 6.6894        | 1.4   | 2500 | 6.6323          | 1.9376 |
| 6.5525        | 1.68  | 3000 | 6.6185          | 1.9383 |
| 6.571         | 1.96  | 3500 | 6.6126          | 1.9580 |
| 6.3363        | 2.24  | 4000 | 6.7869          | 1.9818 |
| 6.5832        | 2.52  | 4500 | 6.9096          | 2.0025 |
| 6.3523        | 2.8   | 5000 | 6.9670          | 1.9878 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
