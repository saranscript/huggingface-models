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
      value: 0.9315407456285054
    - name: Recall
      type: recall
      value: 0.9503534163581285
    - name: F1
      type: f1
      value: 0.9408530489836722
    - name: Accuracy
      type: accuracy
      value: 0.9861511744275033
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0615
- Precision: 0.9315
- Recall: 0.9504
- F1: 0.9409
- Accuracy: 0.9862

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
| 0.084         | 1.0   | 1756 | 0.0683          | 0.9173    | 0.9347 | 0.9259 | 0.9826   |
| 0.0342        | 2.0   | 3512 | 0.0602          | 0.9312    | 0.9470 | 0.9390 | 0.9856   |
| 0.0236        | 3.0   | 5268 | 0.0615          | 0.9315    | 0.9504 | 0.9409 | 0.9862   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
