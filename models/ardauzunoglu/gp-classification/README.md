---
license: mit
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: gp-classification
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# gp-classification

This model is a fine-tuned version of [dbmdz/bert-base-turkish-cased](https://huggingface.co/dbmdz/bert-base-turkish-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0013
- Accuracy: 0.9997
- F1: 0.9997

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| 0.0215        | 1.0   | 956  | 0.0051          | 0.9987   | 0.9987 |
| 0.0033        | 2.0   | 1912 | 0.0088          | 0.9984   | 0.9985 |
| 0.001         | 3.0   | 2868 | 0.0036          | 0.9995   | 0.9995 |
| 0.0005        | 4.0   | 3824 | 0.0012          | 0.9997   | 0.9997 |
| 0.0           | 5.0   | 4780 | 0.0013          | 0.9997   | 0.9997 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
