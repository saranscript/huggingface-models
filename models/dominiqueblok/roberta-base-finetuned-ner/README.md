---
license: mit
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
- name: roberta-base-finetuned-ner
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
      value: 0.9529566113766282
    - name: Recall
      type: recall
      value: 0.9604268983755194
    - name: F1
      type: f1
      value: 0.9566771720212616
    - name: Accuracy
      type: accuracy
      value: 0.988938664048357
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-finetuned-ner

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0492
- Precision: 0.9530
- Recall: 0.9604
- F1: 0.9567
- Accuracy: 0.9889

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
| 0.2031        | 1.0   | 878  | 0.0560          | 0.9381    | 0.9445 | 0.9413 | 0.9858   |
| 0.0446        | 2.0   | 1756 | 0.0480          | 0.9510    | 0.9578 | 0.9544 | 0.9887   |
| 0.0263        | 3.0   | 2634 | 0.0492          | 0.9530    | 0.9604 | 0.9567 | 0.9889   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.0
- Tokenizers 0.10.3
