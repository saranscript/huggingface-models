---
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: spanberta-base-cased-finetuned2-nerconcat
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# spanberta-base-cased-finetuned2-nerconcat

This model is a fine-tuned version of [skimai/spanberta-base-cased](https://huggingface.co/skimai/spanberta-base-cased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1300
- Precision: 0.8409
- Recall: 0.8747
- F1: 0.8575
- Accuracy: 0.9790

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0963        | 1.0   | 11183 | 0.1149          | 0.8048    | 0.8569 | 0.8300 | 0.9735   |
| 0.0623        | 2.0   | 22366 | 0.1123          | 0.8195    | 0.8643 | 0.8413 | 0.9758   |
| 0.0339        | 3.0   | 33549 | 0.1167          | 0.8313    | 0.8752 | 0.8527 | 0.9780   |
| 0.0172        | 4.0   | 44732 | 0.1300          | 0.8409    | 0.8747 | 0.8575 | 0.9790   |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
