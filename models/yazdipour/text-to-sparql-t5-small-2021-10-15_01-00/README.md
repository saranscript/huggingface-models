---
tags:
- generated_from_trainer
model-index:
- name: text-to-sparql-t5-small-2021-10-15_01-00
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-small-2021-10-15_01-00

This model was trained from scratch on the None dataset.

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
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Gen Len | P      | R       | F1     | Bleu-score | Bleu-precisions                                                   | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:------:|:----------:|:-----------------------------------------------------------------:|:-------:|
| No log        | 1.0   | 26   | 4.1488          | 19.0    | 0.2368 | -0.0304 | 0.1003 | 0.8868     | [56.84848484848485, 25.0, 8.88888888888889, 0.041666666666666664] | 0.1851  |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.13.2
- Tokenizers 0.10.3
