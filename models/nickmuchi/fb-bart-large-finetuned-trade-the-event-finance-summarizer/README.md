---
tags:
- summarization
- generated_from_trainer
metrics:
- rouge
model-index:
- name: fb-bart-large-finetuned-trade-the-event-finance-summarizer
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fb-bart-large-finetuned-trade-the-event-finance-summarizer

This model was trained from scratch on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5103
- Rouge1: 57.6289
- Rouge2: 53.0421
- Rougel: 56.54
- Rougelsum: 56.5636

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5.6e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|
| 1.8188        | 1.0   | 1688  | 1.7495          | 37.9629 | 22.0496 | 32.2942 | 32.4631   |
| 1.2551        | 2.0   | 3376  | 1.7559          | 38.5548 | 22.7487 | 32.9304 | 33.0737   |
| 0.8629        | 3.0   | 5064  | 1.9539          | 39.3912 | 22.8503 | 33.2043 | 33.4378   |
| 0.5661        | 4.0   | 6752  | 2.1153          | 39.1514 | 22.8104 | 33.1306 | 33.2955   |
| 0.3484        | 5.0   | 8440  | 2.3289          | 39.0093 | 22.4364 | 32.5868 | 32.7545   |
| 0.2009        | 6.0   | 10128 | 2.5754          | 39.0874 | 22.4444 | 32.6894 | 32.8413   |
| 0.1105        | 7.0   | 11816 | 2.8093          | 39.0905 | 22.4051 | 32.597  | 32.8183   |
| 0.0609        | 8.0   | 13504 | 0.5103          | 57.6289 | 53.0421 | 56.54   | 56.5636   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
