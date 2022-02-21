---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- ag_news
metrics:
- accuracy
model_index:
- name: distilbert-base-uncased-agnews
  results:
  - dataset:
      name: ag_news
      type: ag_news
      args: default
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9473684210526315
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-agnews

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the ag_news dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1652
- Accuracy: 0.9474

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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 2.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.1916        | 1.0   | 3375 | 0.1741          | 0.9412   |
| 0.123         | 2.0   | 6750 | 0.1631          | 0.9483   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
