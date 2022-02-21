---
license: mit
tags:
- generated_from_trainer
model-index:
- name: MTL-roberta-base
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# MTL-roberta-base

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4859

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
| 1.8338        | 1.0   | 98   | 1.6750          |
| 1.7732        | 2.0   | 196  | 1.6229          |
| 1.7208        | 3.0   | 294  | 1.6131          |
| 1.6917        | 4.0   | 392  | 1.5936          |
| 1.6579        | 5.0   | 490  | 1.6183          |
| 1.6246        | 6.0   | 588  | 1.6015          |
| 1.6215        | 7.0   | 686  | 1.5248          |
| 1.5743        | 8.0   | 784  | 1.5454          |
| 1.5621        | 9.0   | 882  | 1.5925          |
| 1.5652        | 10.0  | 980  | 1.5213          |
| 1.5615        | 11.0  | 1078 | 1.4845          |
| 1.5349        | 12.0  | 1176 | 1.5443          |
| 1.5165        | 13.0  | 1274 | 1.5304          |
| 1.5164        | 14.0  | 1372 | 1.4773          |
| 1.5293        | 15.0  | 1470 | 1.5537          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
