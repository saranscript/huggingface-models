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
      value: 0.9274720407485328
    - name: Recall
      type: recall
      value: 0.9370175634858485
    - name: F1
      type: f1
      value: 0.932220367278798
    - name: Accuracy
      type: accuracy
      value: 0.9836370279759162
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0610
- Precision: 0.9275
- Recall: 0.9370
- F1: 0.9322
- Accuracy: 0.9836

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
| 0.2507        | 1.0   | 878  | 0.0714          | 0.9181    | 0.9243 | 0.9212 | 0.9813   |
| 0.0516        | 2.0   | 1756 | 0.0617          | 0.9208    | 0.9325 | 0.9266 | 0.9828   |
| 0.0306        | 3.0   | 2634 | 0.0610          | 0.9275    | 0.9370 | 0.9322 | 0.9836   |


### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
