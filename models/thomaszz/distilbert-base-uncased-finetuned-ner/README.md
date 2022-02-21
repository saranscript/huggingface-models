---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metrics:
    - name: Precision
      type: precision
      value: 0.9244616234124793
    - name: Recall
      type: recall
      value: 0.9364582168027744
    - name: F1
      type: f1
      value: 0.9304212515282871
    - name: Accuracy
      type: accuracy
      value: 0.9833987322668276
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0623
- Precision: 0.9245
- Recall: 0.9365
- F1: 0.9304
- Accuracy: 0.9834

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2377        | 1.0   | 878  | 0.0711          | 0.9176    | 0.9254 | 0.9215 | 0.9813   |
| 0.0514        | 2.0   | 1756 | 0.0637          | 0.9213    | 0.9346 | 0.9279 | 0.9831   |
| 0.031         | 3.0   | 2634 | 0.0623          | 0.9245    | 0.9365 | 0.9304 | 0.9834   |


### Framework versions

- Transformers 4.12.0
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
