---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: distilbert-base-uncased-airlines
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-airlines

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the tasosk/airlines dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3174
- Accuracy: 0.9288
- F1: 0.9289

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 203  | 0.2281          | 0.9164   | 0.9164 |
| No log        | 2.0   | 406  | 0.2676          | 0.9164   | 0.9164 |
| 0.2314        | 3.0   | 609  | 0.3117          | 0.9217   | 0.9217 |
| 0.2314        | 4.0   | 812  | 0.3175          | 0.9270   | 0.9271 |
| 0.08          | 5.0   | 1015 | 0.3174          | 0.9288   | 0.9289 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
