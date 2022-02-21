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
model_index:
- name: bert-large-uncased-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9877039414110284
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-uncased-ner

This model is a fine-tuned version of [bert-large-uncased](https://huggingface.co/bert-large-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0591
- Precision: 0.9465
- Recall: 0.9568
- F1: 0.9517
- Accuracy: 0.9877

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
- train_batch_size: 16
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1702        | 1.0   | 878  | 0.0578          | 0.9202    | 0.9347 | 0.9274 | 0.9836   |
| 0.0392        | 2.0   | 1756 | 0.0601          | 0.9306    | 0.9448 | 0.9377 | 0.9851   |
| 0.0157        | 3.0   | 2634 | 0.0517          | 0.9405    | 0.9544 | 0.9474 | 0.9875   |
| 0.0057        | 4.0   | 3512 | 0.0591          | 0.9465    | 0.9568 | 0.9517 | 0.9877   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
