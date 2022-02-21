---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: bert-base-uncased-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-squad

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4571

## Model description

Most base model weights were frozen leaving only to finetune the last layer (qa outputs) and 3 last layers of the encoder.

## Training and evaluation data

Achieved EM: 76.77388836329234, F1: 85.41893520501723

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 1.2944        | 1.0   | 44262  | 1.3432          |
| 1.0152        | 2.0   | 88524  | 1.3450          |
| 1.0062        | 3.0   | 132786 | 1.4571          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
