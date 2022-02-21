---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: t5-base-finetuned-bbc-headline
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base-finetuned-bbc-headline

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.

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
- train_batch_size: 12
- eval_batch_size: 12
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| No log        | 1.0   | 167  | 2.2978          | 31.8313 | 10.3824 | 29.6182 | 29.4336   | 10.3153 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.12.1
- Tokenizers 0.10.3
