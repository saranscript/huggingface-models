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
- name: fnet-large-finetuned-mrpc
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
      value: 0.8259803921568627
    - name: F1
      type: f1
      value: 0.8798646362098139
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fnet-large-finetuned-mrpc

This model is a fine-tuned version of [google/fnet-large](https://huggingface.co/google/fnet-large) on the GLUE MRPC dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0872
- Accuracy: 0.8260
- F1: 0.8799
- Combined Score: 0.8529

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
| 0.5656        | 1.0   | 917  | 0.6999          | 0.7843   | 0.8581 | 0.8212         |
| 0.3874        | 2.0   | 1834 | 0.7280          | 0.8088   | 0.8691 | 0.8390         |
| 0.1627        | 3.0   | 2751 | 1.1274          | 0.8162   | 0.8780 | 0.8471         |
| 0.0751        | 4.0   | 3668 | 1.0289          | 0.8333   | 0.8870 | 0.8602         |
| 0.0339        | 5.0   | 4585 | 1.0872          | 0.8260   | 0.8799 | 0.8529         |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
