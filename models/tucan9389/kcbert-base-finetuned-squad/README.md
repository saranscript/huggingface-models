---
tags:
- generated_from_trainer
datasets:
- klue
model-index:
- name: kcbert-base-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# kcbert-base-finetuned-squad

This model is a fine-tuned version of [beomi/kcbert-base](https://huggingface.co/beomi/kcbert-base) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6736

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.2221        | 1.0   | 4245  | 1.2784          |
| 0.7673        | 2.0   | 8490  | 1.4099          |
| 0.4479        | 3.0   | 12735 | 1.6736          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
