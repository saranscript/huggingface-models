---
license: mit
tags:
- generated_from_trainer
model-index:
- name: SAE-roberta-base
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# SAE-roberta-base

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6959

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 7
- eval_batch_size: 7
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 1.9847        | 1.0   | 79   | 1.8238          |
| 1.9142        | 2.0   | 158  | 1.8299          |
| 1.8613        | 3.0   | 237  | 1.7636          |
| 1.8384        | 4.0   | 316  | 1.8048          |
| 1.8193        | 5.0   | 395  | 1.7734          |
| 1.7985        | 6.0   | 474  | 1.7271          |
| 1.7758        | 7.0   | 553  | 1.8525          |
| 1.7611        | 8.0   | 632  | 1.7716          |
| 1.7599        | 9.0   | 711  | 1.7913          |
| 1.7118        | 10.0  | 790  | 1.7578          |
| 1.7003        | 11.0  | 869  | 1.7598          |
| 1.7072        | 12.0  | 948  | 1.6942          |
| 1.6511        | 13.0  | 1027 | 1.6955          |
| 1.6802        | 14.0  | 1106 | 1.7837          |
| 1.7048        | 15.0  | 1185 | 1.7377          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
