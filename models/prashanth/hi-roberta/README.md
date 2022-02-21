---
license: mit
tags:
- generated_from_trainer
datasets:
- wnut_17
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: hi-roberta
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wnut_17
      type: wnut_17
      args: semval
    metrics:
    - name: Precision
      type: precision
      value: 0.7018909899888766
    - name: Recall
      type: recall
      value: 0.7620772946859904
    - name: F1
      type: f1
      value: 0.7307469600463232
    - name: Accuracy
      type: accuracy
      value: 0.9491634811100631
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# hi-roberta

This model is a fine-tuned version of [prashanth/xlm-roberta-base-ner](https://huggingface.co/prashanth/xlm-roberta-base-ner) on the wnut_17 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2456
- Precision: 0.7019
- Recall: 0.7621
- F1: 0.7307
- Accuracy: 0.9492

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1409        | 1.0   | 1913 | 0.1970          | 0.6778    | 0.7343 | 0.7049 | 0.9455   |
| 0.0835        | 2.0   | 3826 | 0.2254          | 0.6856    | 0.7452 | 0.7141 | 0.9473   |
| 0.0494        | 3.0   | 5739 | 0.2456          | 0.7019    | 0.7621 | 0.7307 | 0.9492   |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
