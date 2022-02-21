---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-base-finetuned-kaggglenews-fact-corrector-II
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-base-finetuned-kaggglenews-fact-corrector-II

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the None dataset.

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| No log        | 1.0   | 305  | 1.5749          | 27.9313 | 15.1004 | 23.3282 | 25.2336   | 20.0    |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
