---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: bart-base-finetuned-kaggglenews-batch8-epochs3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-base-finetuned-kaggglenews-batch8-epochs3

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5635
- Rouge1: 28.2335
- Rouge2: 16.0201
- Rougel: 24.0315
- Rougelsum: 25.647
- Gen Len: 20.0

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| No log        | 1.0   | 495  | 1.5635          | 28.2335 | 16.0201 | 24.0315 | 25.647    | 20.0    |
| 1.5345        | 2.0   | 990  | 1.5635          | 28.2335 | 16.0201 | 24.0315 | 25.647    | 20.0    |
| 1.531         | 3.0   | 1485 | 1.5635          | 28.2335 | 16.0201 | 24.0315 | 25.647    | 20.0    |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
