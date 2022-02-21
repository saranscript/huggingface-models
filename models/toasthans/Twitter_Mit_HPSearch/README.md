---
license: mit
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: Twitter_Mit_HPSearch
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Twitter_Mit_HPSearch

This model is a fine-tuned version of [bert-base-german-cased](https://huggingface.co/bert-base-german-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8389
- Accuracy: 0.8442

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1.9771872814096894e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 23
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 421  | 0.3838          | 0.8353   |
| 0.4401        | 2.0   | 842  | 0.4340          | 0.8424   |
| 0.2042        | 3.0   | 1263 | 0.6857          | 0.8508   |
| 0.0774        | 4.0   | 1684 | 0.8389          | 0.8442   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
