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
- name: ner_conll2003
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
      value: 0.9772880710440217
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ner_conll2003

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1495
- Precision: 0.8985
- Recall: 0.9130
- F1: 0.9057
- Accuracy: 0.9773

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.423         | 1.0   | 877  | 0.0656          | 0.9158    | 0.9268 | 0.9213 | 0.9818   |
| 0.0575        | 2.0   | 1754 | 0.0574          | 0.9285    | 0.9445 | 0.9364 | 0.9847   |
| 0.0295        | 3.0   | 2631 | 0.0631          | 0.9414    | 0.9456 | 0.9435 | 0.9859   |
| 0.0155        | 4.0   | 3508 | 0.0680          | 0.9395    | 0.9467 | 0.9431 | 0.9860   |
| 0.0097        | 5.0   | 4385 | 0.0694          | 0.9385    | 0.9513 | 0.9449 | 0.9863   |
| 0.0059        | 6.0   | 5262 | 0.0743          | 0.9363    | 0.9471 | 0.9416 | 0.9860   |
| 0.0041        | 7.0   | 6139 | 0.0803          | 0.9371    | 0.9518 | 0.9444 | 0.9862   |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.2
