---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: bert-base-uncased-airlines
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-airlines

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3458
- Accuracy: 0.9021
- F1: 0.9022

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-06
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 7

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 405  | 0.3230          | 0.8754   | 0.8750 |
| 0.4658        | 2.0   | 810  | 0.2738          | 0.8986   | 0.8985 |
| 0.2473        | 3.0   | 1215 | 0.2944          | 0.9110   | 0.9111 |
| 0.2498        | 4.0   | 1620 | 0.3322          | 0.8950   | 0.8949 |
| 0.2174        | 5.0   | 2025 | 0.3342          | 0.9021   | 0.9021 |
| 0.2174        | 6.0   | 2430 | 0.3526          | 0.8986   | 0.8985 |
| 0.2055        | 7.0   | 2835 | 0.3458          | 0.9021   | 0.9022 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
