---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: marian-finetuned-en-map
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# marian-finetuned-en-map

This model is a fine-tuned version of [Helsinki-NLP/opus-mt-en-map](https://huggingface.co/Helsinki-NLP/opus-mt-en-map) on an unknown dataset.
It achieves the following results on the evaluation set:
- eval_loss: 1.0542
- eval_bleu: 30.0673
- eval_runtime: 870.8596
- eval_samples_per_second: 14.467
- eval_steps_per_second: 0.226
- epoch: 2.29
- step: 17104

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
- train_batch_size: 32
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
