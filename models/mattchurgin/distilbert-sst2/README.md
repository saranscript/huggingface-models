---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
model-index:
- name: distilbert-sst2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-sst2

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the glue dataset.
It achieves the following results on the evaluation set:
- eval_loss: 0.4182
- eval_accuracy: 0.8911
- eval_runtime: 1.8021
- eval_samples_per_second: 483.882
- eval_steps_per_second: 60.485
- epoch: 0.8
- step: 6700

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.1
- Datasets 1.17.0
- Tokenizers 0.10.3
