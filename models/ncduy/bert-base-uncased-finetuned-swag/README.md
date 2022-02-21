---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- swag
model_index:
- name: bert-base-uncased-finetuned-swag
  results:
  - dataset:
      name: swag
      type: swag
      args: regular
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-swag

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the swag dataset.
It achieves the following results on the evaluation set:
- eval_loss: 0.6189
- eval_accuracy: 0.7647
- eval_runtime: 274.5502
- eval_samples_per_second: 72.868
- eval_steps_per_second: 4.557
- epoch: 1.0
- step: 4597

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
