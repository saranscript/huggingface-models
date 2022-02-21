---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: bert-base-multilingual-cased-finetuned2-nerconcat
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-multilingual-cased-finetuned2-nerconcat

This model is a fine-tuned version of [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0752
- Precision: 0.9182
- Recall: 0.9203
- F1: 0.9193
- Accuracy: 0.9857

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0605        | 1.0   | 2796  | 0.0669          | 0.8904    | 0.8992 | 0.8948 | 0.9813   |
| 0.0339        | 2.0   | 5592  | 0.0616          | 0.9057    | 0.9181 | 0.9119 | 0.9852   |
| 0.0208        | 3.0   | 8388  | 0.0667          | 0.9089    | 0.9162 | 0.9125 | 0.9851   |
| 0.009         | 4.0   | 11184 | 0.0752          | 0.9182    | 0.9203 | 0.9193 | 0.9857   |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
