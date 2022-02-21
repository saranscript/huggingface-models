---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: distilroberta-base-testingSB-testingSB
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilroberta-base-testingSB-testingSB

This model is a fine-tuned version of [MistahCase/distilroberta-base-testingSB](https://huggingface.co/MistahCase/distilroberta-base-testingSB) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0403

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
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.9885        | 1.0   | 1461 | 1.0564          |
| 0.9963        | 2.0   | 2922 | 1.0278          |
| 0.9903        | 3.0   | 4383 | 1.0403          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
