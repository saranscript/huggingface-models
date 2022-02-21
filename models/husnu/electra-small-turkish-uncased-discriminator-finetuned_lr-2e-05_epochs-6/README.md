---
tags:
- generated_from_trainer
datasets:
- tsquad
model-index:
- name: electra-small-turkish-uncased-discriminator-finetuned_lr-2e-05_epochs-6
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# electra-small-turkish-uncased-discriminator-finetuned_lr-2e-05_epochs-6

This model is a fine-tuned version of [loodos/electra-small-turkish-uncased-discriminator](https://huggingface.co/loodos/electra-small-turkish-uncased-discriminator) on the turkish squad dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0379

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
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 4.128         | 1.0   | 722  | 2.7187          |
| 3.0376        | 2.0   | 1444 | 2.4486          |
| 2.5304        | 3.0   | 2166 | 2.3485          |
| 2.4214        | 4.0   | 2888 | 2.0450          |
| 2.1568        | 5.0   | 3610 | 2.0576          |
| 2.0752        | 6.0   | 4332 | 2.0379          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
