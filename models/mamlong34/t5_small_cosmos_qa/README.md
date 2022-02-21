---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- cosmos_qa
metrics:
- accuracy
model-index:
- name: t5_small_cosmos_qa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5_small_cosmos_qa

This model is a fine-tuned version of [mamlong34/t5_small_race_mutlirc](https://huggingface.co/mamlong34/t5_small_race_mutlirc) on the cosmos_qa dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5614
- Accuracy: 0.6067

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

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.4811        | 1.0   | 3158 | 0.5445          | 0.5548   |
| 0.4428        | 2.0   | 6316 | 0.5302          | 0.5836   |
| 0.3805        | 3.0   | 9474 | 0.5614          | 0.6067   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.12.1
- Tokenizers 0.10.3
