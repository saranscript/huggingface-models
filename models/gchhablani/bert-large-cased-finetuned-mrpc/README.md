---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
- f1
model-index:
- name: bert-large-cased-finetuned-mrpc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE MRPC
      type: glue
      args: mrpc
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.6838235294117647
    - name: F1
      type: f1
      value: 0.8122270742358079
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-cased-finetuned-mrpc

This model is a fine-tuned version of [bert-large-cased](https://huggingface.co/bert-large-cased) on the GLUE MRPC dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6274
- Accuracy: 0.6838
- F1: 0.8122
- Combined Score: 0.7480

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Combined Score |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:--------------:|
| 0.6441        | 1.0   | 917  | 0.6370          | 0.6838   | 0.8122 | 0.7480         |
| 0.6451        | 2.0   | 1834 | 0.6553          | 0.6838   | 0.8122 | 0.7480         |
| 0.6428        | 3.0   | 2751 | 0.6332          | 0.6838   | 0.8122 | 0.7480         |
| 0.6476        | 4.0   | 3668 | 0.6248          | 0.6838   | 0.8122 | 0.7480         |
| 0.6499        | 5.0   | 4585 | 0.6274          | 0.6838   | 0.8122 | 0.7480         |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
