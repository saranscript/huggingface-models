---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: bart-large-chinese-cnhdwriter
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-large-chinese-cnhdwriter

This model is a fine-tuned version of [fnlp/bart-large-chinese](https://huggingface.co/fnlp/bart-large-chinese) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3859
- Rouge1: 16.8496
- Rouge2: 2.5548
- Rougel: 16.8123
- Rougelsum: 16.8056
- Gen Len: 18.9357

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
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 1.2119        | 1.0   | 62716  | 1.1876          | 15.3858 | 2.1251 | 15.3709 | 15.3705   | 18.7269 |
| 1.0847        | 2.0   | 125432 | 1.3353          | 13.7743 | 1.9047 | 13.7664 | 13.7421   | 18.6183 |
| 0.6995        | 3.0   | 188148 | 1.2209          | 16.6797 | 2.3979 | 16.6258 | 16.6368   | 18.8953 |
| 0.4819        | 4.0   | 250864 | 1.3859          | 16.8496 | 2.5548 | 16.8123 | 16.8056   | 18.9357 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
