---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: reddit-bert-text_20
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# reddit-bert-text_20

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.4702
- Perplexity: 11.82

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
| 2.9383        | 1.0   | 947  | 2.5420          |
| 2.6448        | 2.0   | 1894 | 2.5241          |
| 2.586         | 3.0   | 2841 | 2.4833          |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu113
- Datasets 1.16.1
- Tokenizers 0.10.3
