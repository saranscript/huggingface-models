---
license: mit
tags:
- generated_from_trainer
datasets:
- conll2002
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: xlm-roberta-base-finetuned-ner-false
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2002
      type: conll2002
      args: es
    metrics:
    - name: Precision
      type: precision
      value: 0.8630790190735694
    - name: Recall
      type: recall
      value: 0.8733915441176471
    - name: F1
      type: f1
      value: 0.868204659661946
    - name: Accuracy
      type: accuracy
      value: 0.9799142149915916
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-base-finetuned-ner-false

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the conll2002 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1358
- Precision: 0.8631
- Recall: 0.8734
- F1: 0.8682
- Accuracy: 0.9799

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
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.086         | 1.0   | 4162  | 0.1333          | 0.8411    | 0.8318 | 0.8364 | 0.9750   |
| 0.0617        | 2.0   | 8324  | 0.1147          | 0.8482    | 0.8631 | 0.8556 | 0.9773   |
| 0.0384        | 3.0   | 12486 | 0.1144          | 0.8643    | 0.8736 | 0.8689 | 0.9796   |
| 0.023         | 4.0   | 16648 | 0.1358          | 0.8631    | 0.8734 | 0.8682 | 0.9799   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
