---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: t5_small_race_mutlirc
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5_small_race_mutlirc

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5760
- Accuracy: 0.5259

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 8
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step  | Accuracy | Validation Loss |
|:-------------:|:-----:|:-----:|:--------:|:---------------:|
| 0.6043        | 1.0   | 14141 | 0.4832   | 0.5925          |
| 0.5647        | 2.0   | 28282 | 0.5152   | 0.5659          |
| 0.5237        | 3.0   | 42423 | 0.5760   | 0.5259          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.12.1
- Tokenizers 0.10.3
