---
license: mit
tags:
- generated_from_trainer
datasets:
- wnut_17
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: xlm-roberta-base-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wnut_17
      type: wnut_17
      args: semval
    metrics:
    - name: Precision
      type: precision
      value: 0.7800724358480389
    - name: Recall
      type: recall
      value: 0.8089986414129305
    - name: F1
      type: f1
      value: 0.7942722636327972
    - name: Accuracy
      type: accuracy
      value: 0.9520096154243302
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-base-ner

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the wnut_17 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1671
- Precision: 0.7801
- Recall: 0.8090
- F1: 0.7943
- Accuracy: 0.9520

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

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2022        | 1.0   | 21038 | 0.1786          | 0.7275    | 0.7570 | 0.7419 | 0.9414   |
| 0.1366        | 2.0   | 42076 | 0.1598          | 0.7542    | 0.8052 | 0.7789 | 0.9484   |
| 0.0973        | 3.0   | 63114 | 0.1671          | 0.7801    | 0.8090 | 0.7943 | 0.9520   |


### Framework versions

- Transformers 4.16.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.11.0
