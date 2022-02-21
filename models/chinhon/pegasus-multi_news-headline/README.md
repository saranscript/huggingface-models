---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-multi_news-headline
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-multi_news-headline

This model is a fine-tuned version of [google/pegasus-multi_news](https://huggingface.co/google/pegasus-multi_news) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4421
- Rouge1: 41.616
- Rouge2: 22.922
- Rougel: 35.2189
- Rougelsum: 35.3561
- Gen Len: 33.9532

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
- train_batch_size: 1
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 1.6637        | 1.0   | 31200 | 1.4877          | 41.0996 | 22.579  | 34.9311 | 35.0611   | 34.3431 |
| 1.4395        | 2.0   | 62400 | 1.4388          | 41.6075 | 22.8274 | 35.2051 | 35.3526   | 33.7965 |
| 1.3137        | 3.0   | 93600 | 1.4421          | 41.616  | 22.922  | 35.2189 | 35.3561   | 33.9532 |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
