---
license: apache-2.0
tags:
- summarization
- generated_from_trainer
metrics:
- rouge
model-index:
- name: mt5-finetuned-amazon-en-es
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-finetuned-amazon-en-es

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0285
- Rouge1: 16.9728
- Rouge2: 8.2969
- Rougel: 16.8366
- Rougelsum: 16.851
- Gen Len: 10.1597

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

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 7.1016        | 1.0   | 1209 | 3.3069          | 13.9858 | 5.8437 | 13.6053 | 13.5125   | 8.3782  |
| 3.898         | 2.0   | 2418 | 3.1567          | 16.6706 | 8.6393 | 16.2882 | 16.2249   | 9.7521  |
| 3.5915        | 3.0   | 3627 | 3.0928          | 17.111  | 8.3921 | 16.9139 | 16.7805   | 10.3445 |
| 3.4174        | 4.0   | 4836 | 3.0482          | 16.9728 | 8.3066 | 16.8868 | 16.8485   | 10.3151 |
| 3.3258        | 5.0   | 6045 | 3.0375          | 16.5972 | 8.2621 | 16.3524 | 16.3093   | 10.0672 |
| 3.2427        | 6.0   | 7254 | 3.0232          | 17.3009 | 8.6087 | 17.0782 | 17.0105   | 10.0756 |
| 3.2009        | 7.0   | 8463 | 3.0302          | 16.9284 | 8.6569 | 16.7885 | 16.7784   | 10.2143 |
| 3.1838        | 8.0   | 9672 | 3.0285          | 16.9728 | 8.2969 | 16.8366 | 16.851    | 10.1597 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.1+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
