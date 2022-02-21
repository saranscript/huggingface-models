---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: reddit-bert-text2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# reddit-bert-text2

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.4969
- Perplexity: 12.14

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
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.8378        | 1.0   | 1007 | 2.6379          |
| 2.6493        | 2.0   | 2014 | 2.5655          |
| 2.5561        | 3.0   | 3021 | 2.5382          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu113
- Datasets 1.16.1
- Tokenizers 0.10.3
