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
      value: 0.9310572323932047
    - name: Recall
      type: recall
      value: 0.9500168293503871
    - name: F1
      type: f1
      value: 0.9404414827155352
    - name: Accuracy
      type: accuracy
      value: 0.9865191028433508
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0590
- Precision: 0.9311
- Recall: 0.9500
- F1: 0.9404
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
| 0.0874        | 1.0   | 1756 | 0.0635          | 0.9211    | 0.9369 | 0.9289 | 0.9835   |
| 0.0376        | 2.0   | 3512 | 0.0618          | 0.9342    | 0.9485 | 0.9413 | 0.9858   |
| 0.0226        | 3.0   | 5268 | 0.0590          | 0.9311    | 0.9500 | 0.9404 | 0.9865   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
