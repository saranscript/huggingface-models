---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- conll2012
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: ner_conll2012
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2012
      type: conll2012
      args: conll2012
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9751241645956311
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ner_conll2012

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the conll2012 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1094
- Precision: 0.8338
- Recall: 0.8633
- F1: 0.8483
- Accuracy: 0.9751

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2459        | 1.0   | 7238  | 0.0969          | 0.8236    | 0.8771 | 0.8495 | 0.9706   |
| 0.0632        | 2.0   | 14476 | 0.0964          | 0.8466    | 0.8759 | 0.8610 | 0.9727   |
| 0.0366        | 3.0   | 21714 | 0.1031          | 0.8528    | 0.8799 | 0.8662 | 0.9739   |
| 0.0206        | 4.0   | 28952 | 0.1190          | 0.8557    | 0.8818 | 0.8685 | 0.9741   |
| 0.0119        | 5.0   | 36190 | 0.1282          | 0.8608    | 0.8761 | 0.8684 | 0.9742   |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.2
