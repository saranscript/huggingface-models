---
license: mit
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: bert-small-pretrained-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-small-pretrained-finetuned-squad

This model is a fine-tuned version of [anas-awadalla/bert-small-pretrained-on-squad](https://huggingface.co/anas-awadalla/bert-small-pretrained-on-squad) on the squad dataset.

- "exact_match": 72.20435193945127
- "f1": 81.31832229156294

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
- num_epochs: 3.0

### Training results



### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
