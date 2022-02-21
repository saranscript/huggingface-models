---
license: mit
tags:
- generated_from_trainer
datasets:
- imdb
metrics:
- accuracy
model-index:
- name: roberta-base-finetuned-imdb
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: imdb
      type: imdb
      args: plain_text
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9552
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-finetuned-imdb

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the imdb dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1783
- Accuracy: 0.9552

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
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.1904        | 1.0   | 1563 | 0.1423          | 0.9517   |
| 0.1187        | 2.0   | 3126 | 0.1783          | 0.9552   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
