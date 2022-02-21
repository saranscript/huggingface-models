---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased-finetuned-vi-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-vi-infovqa

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.5470

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
| No log        | 0.21  | 100  | 4.2058          |
| No log        | 0.43  | 200  | 4.0210          |
| No log        | 0.64  | 300  | 4.0454          |
| No log        | 0.85  | 400  | 3.7557          |
| 4.04          | 1.07  | 500  | 3.8257          |
| 4.04          | 1.28  | 600  | 3.7713          |
| 4.04          | 1.49  | 700  | 3.6075          |
| 4.04          | 1.71  | 800  | 3.6155          |
| 4.04          | 1.92  | 900  | 3.5470          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
