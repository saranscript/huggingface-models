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
      value: 0.9255649091714665
    - name: Recall
      type: recall
      value: 0.9347801767535519
    - name: F1
      type: f1
      value: 0.9301497189291478
    - name: Accuracy
      type: accuracy
      value: 0.9837164598789457
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0613
- Precision: 0.9256
- Recall: 0.9348
- F1: 0.9301
- Accuracy: 0.9837

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
| 0.2414        | 1.0   | 878  | 0.0702          | 0.9097    | 0.9200 | 0.9148 | 0.9804   |
| 0.0521        | 2.0   | 1756 | 0.0609          | 0.9190    | 0.9327 | 0.9258 | 0.9828   |
| 0.0308        | 3.0   | 2634 | 0.0613          | 0.9256    | 0.9348 | 0.9301 | 0.9837   |


### Framework versions

- Transformers 4.11.0
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
