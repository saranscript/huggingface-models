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
- name: distilbert-base-uncased-finetuned-ner
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
      value: 0.9281908990011098
    - name: Recall
      type: recall
      value: 0.9355632621098557
    - name: F1
      type: f1
      value: 0.9318624993035824
    - name: Accuracy
      type: accuracy
      value: 0.9837641190207635
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0629
- Precision: 0.9282
- Recall: 0.9356
- F1: 0.9319
- Accuracy: 0.9838

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
| 0.2406        | 1.0   | 878  | 0.0721          | 0.9072    | 0.9172 | 0.9122 | 0.9801   |
| 0.0529        | 2.0   | 1756 | 0.0637          | 0.9166    | 0.9318 | 0.9241 | 0.9826   |
| 0.0315        | 3.0   | 2634 | 0.0629          | 0.9282    | 0.9356 | 0.9319 | 0.9838   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
