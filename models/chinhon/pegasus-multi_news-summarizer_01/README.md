---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-multi_news-summarizer_01
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-multi_news-summarizer_01

This model is a fine-tuned version of [google/pegasus-multi_news](https://huggingface.co/google/pegasus-multi_news) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2794
- Rouge1: 52.1693
- Rouge2: 34.8989
- Rougel: 41.2385
- Rougelsum: 48.4365
- Gen Len: 98.6433

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
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len  |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:--------:|
| 1.3936        | 1.0   | 16113 | 1.2972          | 51.5747 | 34.2062 | 40.7279 | 47.7783   | 95.0004  |
| 1.3664        | 2.0   | 32226 | 1.2817          | 52.1077 | 34.8189 | 41.1614 | 48.3894   | 100.3265 |
| 1.3002        | 3.0   | 48339 | 1.2794          | 52.1693 | 34.8989 | 41.2385 | 48.4365   | 98.6433  |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
