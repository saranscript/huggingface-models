---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: t5-vietnamese-text-summarization
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-vietnamese-text-summarization

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.2500
- Rouge1: 3.0732
- Rouge2: 2.6051
- Rougel: 2.5601
- Rougelsum: 2.871

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:-------:|:-------:|:---------:|
| 4.1645        | 1.0   | 35   | 2.9417          | 9.3313  | 5.3457  | 8.3892  | 8.8682    |
| 3.0413        | 2.0   | 70   | 2.5201          | 17.3676 | 12.5506 | 14.937  | 16.3599   |
| 3.4124        | 3.0   | 105  | 2.4002          | 17.5043 | 12.97   | 15.2764 | 16.4665   |
| 2.652         | 4.0   | 140  | 2.3413          | 15.2824 | 11.6981 | 13.118  | 14.4374   |
| 2.4939        | 5.0   | 175  | 2.3161          | 10.1775 | 7.8212  | 8.6508  | 9.5131    |
| 2.2044        | 6.0   | 210  | 2.2885          | 6.3708  | 4.9655  | 5.3057  | 5.8851    |
| 2.129         | 7.0   | 245  | 2.2747          | 4.1349  | 3.2928  | 3.3036  | 3.7403    |
| 2.7997        | 8.0   | 280  | 2.2592          | 3.3715  | 2.8781  | 2.7802  | 3.1013    |
| 2.5278        | 9.0   | 315  | 2.2541          | 3.3715  | 2.8781  | 2.7802  | 3.1013    |
| 2.6236        | 10.0  | 350  | 2.2500          | 3.0732  | 2.6051  | 2.5601  | 2.871     |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
