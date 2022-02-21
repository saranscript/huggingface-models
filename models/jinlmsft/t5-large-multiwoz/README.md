---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: t5-large-multiwoz
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-large-multiwoz

This model is a fine-tuned version of [t5-large](https://huggingface.co/t5-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0064
- Acc: 1.0
- True Num: 56671
- Num: 56776

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 16
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Acc  | True Num | Num   |
|:-------------:|:-----:|:----:|:---------------:|:----:|:--------:|:-----:|
| 0.1261        | 1.13  | 1000 | 0.0933          | 0.98 | 55574    | 56776 |
| 0.0951        | 2.25  | 2000 | 0.0655          | 0.98 | 55867    | 56776 |
| 0.0774        | 3.38  | 3000 | 0.0480          | 0.99 | 56047    | 56776 |
| 0.0584        | 4.51  | 4000 | 0.0334          | 0.99 | 56252    | 56776 |
| 0.042         | 5.64  | 5000 | 0.0222          | 0.99 | 56411    | 56776 |
| 0.0329        | 6.76  | 6000 | 0.0139          | 1.0  | 56502    | 56776 |
| 0.0254        | 7.89  | 7000 | 0.0094          | 1.0  | 56626    | 56776 |
| 0.0214        | 9.02  | 8000 | 0.0070          | 1.0  | 56659    | 56776 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
