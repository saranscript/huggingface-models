---
license: apache-2.0
tags:
- summarization
- generated_from_trainer
metrics:
- rouge
model-index:
- name: mt5-small-finetuned-amazon-en-es
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-amazon-en-es

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0393
- Rouge1: 17.3313
- Rouge2: 8.1251
- Rougel: 17.0359
- Rougelsum: 16.9503

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

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|
| 6.6665        | 1.0   | 1209 | 3.2917          | 13.908  | 5.5316 | 13.4368 | 13.4302   |
| 3.8961        | 2.0   | 2418 | 3.1711          | 16.247  | 8.7234 | 15.7703 | 15.6964   |
| 3.5801        | 3.0   | 3627 | 3.0917          | 17.3455 | 8.2467 | 16.8631 | 16.8147   |
| 3.4258        | 4.0   | 4836 | 3.0583          | 16.0978 | 7.83   | 15.8065 | 15.7725   |
| 3.3154        | 5.0   | 6045 | 3.0573          | 17.5531 | 8.7811 | 17.2252 | 17.2055   |
| 3.2438        | 6.0   | 7254 | 3.0479          | 17.2072 | 8.0951 | 17.025  | 16.9644   |
| 3.2024        | 7.0   | 8463 | 3.0377          | 17.3692 | 8.1843 | 17.019  | 17.0006   |
| 3.1745        | 8.0   | 9672 | 3.0393          | 17.3313 | 8.1251 | 17.0359 | 16.9503   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
