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
      value: 0.9361244415025649
    - name: Recall
      type: recall
      value: 0.9520363513968361
    - name: F1
      type: f1
      value: 0.9440133500208594
    - name: Accuracy
      type: accuracy
      value: 0.986489668570083
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0642
- Precision: 0.9361
- Recall: 0.9520
- F1: 0.9440
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
| 0.0874        | 1.0   | 1756 | 0.0696          | 0.9177    | 0.9344 | 0.9260 | 0.9818   |
| 0.0324        | 2.0   | 3512 | 0.0634          | 0.9362    | 0.9490 | 0.9426 | 0.9856   |
| 0.0226        | 3.0   | 5268 | 0.0642          | 0.9361    | 0.9520 | 0.9440 | 0.9865   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0a0+0aef44c
- Datasets 1.18.3
- Tokenizers 0.11.0
