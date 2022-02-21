---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: model1_test
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# model1_test

This model is a fine-tuned version of [DaNLP/da-bert-hatespeech-detection](https://huggingface.co/DaNLP/da-bert-hatespeech-detection) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1816
- Accuracy: 0.9667
- F1: 0.3548

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 150  | 0.1128          | 0.9667   | 0.2    |
| No log        | 2.0   | 300  | 0.1666          | 0.9684   | 0.2963 |
| No log        | 3.0   | 450  | 0.1816          | 0.9667   | 0.3548 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
