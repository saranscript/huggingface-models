---
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: bert-small-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-small-finetuned-squad

This model is a fine-tuned version of [prajjwal1/bert-small](https://huggingface.co/prajjwal1/bert-small) on the squad dataset.
It achieves the following results on the evaluation set:
- eval_loss: 1.3138
- eval_runtime: 46.6577
- eval_samples_per_second: 231.13
- eval_steps_per_second: 14.446
- epoch: 4.0
- step: 22132

{'exact_match': 71.05960264900662, 'f1': 80.8260245470904}

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
- num_epochs: 20

### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
