---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- race
metrics:
- accuracy
model-index:
- name: t5_large_race_cosmos_qa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5_large_race_cosmos_qa

This model is a fine-tuned version of [t5-large](https://huggingface.co/t5-large) on the race dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4382
- Accuracy: 0.8023

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 4
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 8
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step  | Accuracy | Validation Loss |
|:-------------:|:-----:|:-----:|:--------:|:---------------:|
| 0.3513        | 1.0   | 10983 | 0.7714   | 0.3165          |
| 0.2109        | 2.0   | 21966 | 0.7986   | 0.3329          |
| 0.0929        | 3.0   | 32949 | 0.4382   | 0.8023          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0
- Datasets 1.14.0
- Tokenizers 0.10.3
