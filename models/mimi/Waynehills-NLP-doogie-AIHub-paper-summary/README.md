---
tags:
- generated_from_trainer
model-index:
- name: Waynehills-NLP-doogie-AIHub-paper-summary
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Waynehills-NLP-doogie-AIHub-paper-summary

This model is a fine-tuned version of [mimi/Waynehills-NLP-doogie](https://huggingface.co/mimi/Waynehills-NLP-doogie) on the None dataset.
It achieves the following results on the evaluation set:
- eval_loss: 2.6206
- eval_runtime: 309.223
- eval_samples_per_second: 38.167
- eval_steps_per_second: 4.773
- epoch: 3.75
- step: 60000

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
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Framework versions

- Transformers 4.12.2
- Pytorch 1.10.0+cu111
- Datasets 1.5.0
- Tokenizers 0.10.3
