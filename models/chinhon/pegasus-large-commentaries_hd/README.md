---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-large-commentaries_hd
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-large-commentaries_hd

This model is a fine-tuned version of [google/pegasus-large](https://huggingface.co/google/pegasus-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.5453
- Rouge1: 26.3475
- Rouge2: 9.5095
- Rougel: 22.6367
- Rougelsum: 22.8127
- Gen Len: 14.4789

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
- train_batch_size: 1
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.5718        | 1.0   | 4710  | 2.5277          | 25.1384 | 8.6528 | 21.3443 | 21.5289   | 15.3268 |
| 2.4034        | 2.0   | 9420  | 2.4973          | 25.9298 | 9.2238 | 22.3192 | 22.4817   | 14.2243 |
| 2.2093        | 3.0   | 14130 | 2.5013          | 26.6036 | 9.7482 | 22.8409 | 23.0077   | 14.2263 |
| 2.0518        | 4.0   | 18840 | 2.5272          | 26.4723 | 9.6599 | 22.7439 | 22.9201   | 14.38   |
| 1.9906        | 5.0   | 23550 | 2.5453          | 26.3475 | 9.5095 | 22.6367 | 22.8127   | 14.4789 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
