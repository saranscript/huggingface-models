---
license: apache-2.0
tags:
- summarization
- generated_from_trainer
metrics:
- rouge
model-index:
- name: mt5-small-finetuned-amazon-en-es-v1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-amazon-en-es-v1

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0393
- Rouge1: 17.2431
- Rouge2: 8.087
- Rougel: 16.9132
- Rougelsum: 16.9485

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5.6e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|
| 6.6665        | 1.0   | 1209 | 3.2917          | 13.8229 | 5.5115 | 13.3845 | 13.4326   |
| 3.8961        | 2.0   | 2418 | 3.1711          | 16.2336 | 8.5449 | 15.6123 | 15.5944   |
| 3.5801        | 3.0   | 3627 | 3.0917          | 17.3138 | 8.1576 | 16.709  | 16.6737   |
| 3.4258        | 4.0   | 4836 | 3.0583          | 16.1301 | 7.7461 | 15.7185 | 15.7575   |
| 3.3154        | 5.0   | 6045 | 3.0573          | 17.5471 | 8.7643 | 17.2062 | 17.1174   |
| 3.2438        | 6.0   | 7254 | 3.0479          | 17.161  | 8.0785 | 16.8794 | 16.8996   |
| 3.2024        | 7.0   | 8463 | 3.0377          | 17.2455 | 8.1524 | 16.8894 | 16.9402   |
| 3.1745        | 8.0   | 9672 | 3.0393          | 17.2431 | 8.087  | 16.9132 | 16.9485   |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
