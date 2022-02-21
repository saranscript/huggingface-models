---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
- f1
model-index:
- name: test-train
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: mrpc
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8455882352941176
    - name: F1
      type: f1
      value: 0.8926746166950595
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# test-train

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7268
- Accuracy: 0.8456
- F1: 0.8927

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 459  | 0.3470          | 0.8627   | 0.9014 |
| 0.4987        | 2.0   | 918  | 0.5782          | 0.8382   | 0.8914 |
| 0.2796        | 3.0   | 1377 | 0.7268          | 0.8456   | 0.8927 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
