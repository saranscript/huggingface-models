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
- name: bert-finetuned-ner
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
      value: 0.9407949442873773
    - name: Recall
      type: recall
      value: 0.9520363513968361
    - name: F1
      type: f1
      value: 0.9463822668339608
    - name: Accuracy
      type: accuracy
      value: 0.9865485371166186
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0603
- Precision: 0.9408
- Recall: 0.9520
- F1: 0.9464
- Accuracy: 0.9865

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

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0884        | 1.0   | 1756 | 0.0658          | 0.9145    | 0.9337 | 0.9240 | 0.9827   |
| 0.0375        | 2.0   | 3512 | 0.0618          | 0.9366    | 0.9490 | 0.9427 | 0.9864   |
| 0.0216        | 3.0   | 5268 | 0.0603          | 0.9408    | 0.9520 | 0.9464 | 0.9865   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
