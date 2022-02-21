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
      value: 0.9334444444444444
    - name: Recall
      type: recall
      value: 0.9398142969012194
    - name: F1
      type: f1
      value: 0.9366185406098445
    - name: Accuracy
      type: accuracy
      value: 0.9845425516704529
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0727
- Precision: 0.9334
- Recall: 0.9398
- F1: 0.9366
- Accuracy: 0.9845

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
| 0.0271        | 1.0   | 878  | 0.0656          | 0.9339    | 0.9339 | 0.9339 | 0.9840   |
| 0.0136        | 2.0   | 1756 | 0.0703          | 0.9268    | 0.9380 | 0.9324 | 0.9838   |
| 0.008         | 3.0   | 2634 | 0.0727          | 0.9334    | 0.9398 | 0.9366 | 0.9845   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
