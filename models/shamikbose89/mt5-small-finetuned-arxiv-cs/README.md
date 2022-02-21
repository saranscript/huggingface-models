---
license: apache-2.0
tags:
- generated_from_trainer
- summarization
metrics:
- rouge
model-index:
- name: mt5-small-finetuned-arxiv-cs
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-arxiv-cs

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on a subset of the arxiv dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6922
- Rouge1: 0.7734
- Rouge2: 0.2865
- Rougel: 0.6665
- Rougelsum: 0.6743

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
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1 | Rouge2 | Rougel | Rougelsum |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|:------:|:---------:|
| 14.0947       | 1.0   | 500  | 2.7666          | 1.2101 | 0.459  | 1.1426 | 1.1385    |
| 2.8524        | 2.0   | 1000 | 1.8208          | 0.0    | 0.0    | 0.0    | 0.0       |
| 2.2623        | 3.0   | 1500 | 1.6922          | 0.7734 | 0.2865 | 0.6665 | 0.6743    |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
