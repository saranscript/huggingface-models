---
license: mit
tags:
- generated_from_trainer
datasets:
- harem
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: bert-base-portuguese-cased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: harem
      type: harem
      args: default
    metrics:
    - name: Precision
      type: precision
      value: 0.0
    - name: Recall
      type: recall
      value: 0.0
    - name: F1
      type: f1
      value: 0.0
    - name: Accuracy
      type: accuracy
      value: 0.7333736396614269
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-portuguese-cased-finetuned-ner

This model is a fine-tuned version of [neuralmind/bert-base-portuguese-cased](https://huggingface.co/neuralmind/bert-base-portuguese-cased) on the harem dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2948
- Precision: 0.0
- Recall: 0.0
- F1: 0.0
- Accuracy: 0.7334

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

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1  | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:---:|:--------:|
| No log        | 1.0   | 8    | 1.7381          | 0.0       | 0.0    | 0.0 | 0.7334   |
| No log        | 2.0   | 16   | 1.3301          | 0.0       | 0.0    | 0.0 | 0.7334   |
| No log        | 3.0   | 24   | 1.2948          | 0.0       | 0.0    | 0.0 | 0.7334   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
