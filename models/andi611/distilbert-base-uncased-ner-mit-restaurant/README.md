---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- mit_restaurant
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: distilbert-base-uncased-ner-mit-restaurant
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: mit_restaurant
      type: mit_restaurant
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9118988661540467
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-ner-mit-restaurant

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the mit_restaurant dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3097
- Precision: 0.7874
- Recall: 0.8104
- F1: 0.7988
- Accuracy: 0.9119

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
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 431  | 0.4575          | 0.6220    | 0.6856 | 0.6523 | 0.8650   |
| 1.1705        | 2.0   | 862  | 0.3183          | 0.7747    | 0.7953 | 0.7848 | 0.9071   |
| 0.3254        | 3.0   | 1293 | 0.3163          | 0.7668    | 0.8021 | 0.7841 | 0.9058   |
| 0.2287        | 4.0   | 1724 | 0.3097          | 0.7874    | 0.8104 | 0.7988 | 0.9119   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
