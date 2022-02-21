---
license: cc-by-nc-sa-4.0
tags:
- generated_from_trainer
model-index:
- name: layoutlmv2-base-uncased-finetuned-vi-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# layoutlmv2-base-uncased-finetuned-vi-infovqa

This model is a fine-tuned version of [microsoft/layoutlmv2-base-uncased](https://huggingface.co/microsoft/layoutlmv2-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 4.3332

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 0.33  | 100  | 5.3461          |
| No log        | 0.66  | 200  | 4.9734          |
| No log        | 0.99  | 300  | 4.6074          |
| No log        | 1.32  | 400  | 4.4548          |
| 4.6355        | 1.65  | 500  | 4.3831          |
| 4.6355        | 1.98  | 600  | 4.3332          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.8.0+cu101
- Datasets 1.17.0
- Tokenizers 0.10.3
