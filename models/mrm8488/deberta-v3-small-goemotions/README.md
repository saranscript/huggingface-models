---
license: mit
tags:
- generated_from_trainer
metrics:
- f1
model-index:
- name: deberta-v3-snall-goemotions
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# deberta-v3-snall-goemotions

This model is a fine-tuned version of [microsoft/deberta-v3-small](https://huggingface.co/microsoft/deberta-v3-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5638
- F1: 0.4241

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | F1     |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.614         | 1.0   | 3082  | 1.5577          | 0.3663 |
| 1.4338        | 2.0   | 6164  | 1.5580          | 0.4084 |
| 1.2936        | 3.0   | 9246  | 1.5006          | 0.4179 |
| 1.1531        | 4.0   | 12328 | 1.5348          | 0.4276 |
| 1.0536        | 5.0   | 15410 | 1.5638          | 0.4241 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
