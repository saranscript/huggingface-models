---
license: agpl-3.0
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
language: 
- en
- is
model-index:
- name: XLMR-ENIS-finetuned-ner
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
      value: 0.9398313331170938
    - name: Recall
      type: recall
      value: 0.9517943664285128
    - name: F1
      type: f1
      value: 0.9457750214207026
    - name: Accuracy
      type: accuracy
      value: 0.9853686150987764
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLMR-ENIS-finetuned-ner

This model is a fine-tuned version of [vesteinn/XLMR-ENIS](https://huggingface.co/vesteinn/XLMR-ENIS) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0671
- Precision: 0.9398
- Recall: 0.9518
- F1: 0.9458
- Accuracy: 0.9854

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
| 0.2825        | 1.0   | 878  | 0.0712          | 0.9220    | 0.9379 | 0.9299 | 0.9815   |
| 0.0688        | 2.0   | 1756 | 0.0689          | 0.9354    | 0.9477 | 0.9415 | 0.9839   |
| 0.039         | 3.0   | 2634 | 0.0671          | 0.9398    | 0.9518 | 0.9458 | 0.9854   |


### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
