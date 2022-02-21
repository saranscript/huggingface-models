---
tags:
- generated_from_trainer
datasets:
- wmt16_en_ro_pre_processed
model-index:
- name: t5-tiny-random-length-128-learning_rate-2e-05-weight_decay-0.01-finetuned-en-to-ro-TRAIN_EPOCHS-1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-tiny-random-length-128-learning_rate-2e-05-weight_decay-0.01-finetuned-en-to-ro-TRAIN_EPOCHS-1

This model is a fine-tuned version of [patrickvonplaten/t5-tiny-random](https://huggingface.co/patrickvonplaten/t5-tiny-random) on the wmt16_en_ro_pre_processed dataset.

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
- num_epochs: 1
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
