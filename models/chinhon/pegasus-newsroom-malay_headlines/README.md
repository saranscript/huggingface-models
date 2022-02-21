---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-newsroom-malay_headlines
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-newsroom-malay_headlines

This model is a fine-tuned version of [google/pegasus-newsroom](https://huggingface.co/google/pegasus-newsroom) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6603
- Rouge1: 42.6667
- Rouge2: 22.8739
- Rougel: 38.6684
- Rougelsum: 38.6928
- Gen Len: 34.7995

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 1.9713        | 1.0   | 15310 | 1.8121          | 41.1469 | 21.5262 | 37.3081 | 37.3377   | 35.0939 |
| 1.7917        | 2.0   | 30620 | 1.6913          | 42.4027 | 22.6089 | 38.4471 | 38.4699   | 34.8149 |
| 1.7271        | 3.0   | 45930 | 1.6603          | 42.6667 | 22.8739 | 38.6684 | 38.6928   | 34.7995 |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
