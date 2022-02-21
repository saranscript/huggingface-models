---
metrics:
- rouge

model-index:
- name: gq-indo-k
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# gq-indo-k

This model was trained from scratch on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.7905
- Rouge1: 22.5734
- Rouge2: 6.555
- Rougel: 20.9491
- Rougelsum: 20.9509
- Gen Len: 12.0767

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
- train_batch_size: 10
- eval_batch_size: 10
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.9355        | 1.0   | 13032 | 2.8563          | 22.4828 | 6.5456 | 20.8782 | 20.8772   | 11.915  |
| 2.825         | 2.0   | 26064 | 2.7993          | 22.547  | 6.5815 | 20.8937 | 20.8973   | 12.0886 |
| 2.7631        | 3.0   | 39096 | 2.7905          | 22.5734 | 6.555  | 20.9491 | 20.9509   | 12.0767 |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.0
- Datasets 1.11.0
- Tokenizers 0.10.3
