---
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: ft_electra-small-turkish-uncased-discriminator_lr-2e-1_epochs-1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

This model is a fine-tuned version of [loodos/electra-small-turkish-uncased-discriminator](https://huggingface.co/loodos/electra-small-turkish-uncased-discriminator) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 5.9506

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.2
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 5.951         | 1.0   | 5818 | 5.9506          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
