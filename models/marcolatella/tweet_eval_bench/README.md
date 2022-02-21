---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- tweet_eval
metrics:
- accuracy
model-index:
- name: prova_Classi
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: tweet_eval
      type: tweet_eval
      args: sentiment
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.716
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# prova_Classi

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the tweet_eval dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5530
- Accuracy: 0.716

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.00013441028267541125
- train_batch_size: 32
- eval_batch_size: 16
- seed: 17
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.7022        | 1.0   | 1426 | 0.6581          | 0.7105   |
| 0.5199        | 2.0   | 2852 | 0.6835          | 0.706    |
| 0.2923        | 3.0   | 4278 | 0.7941          | 0.7075   |
| 0.1366        | 4.0   | 5704 | 1.0761          | 0.7115   |
| 0.0645        | 5.0   | 7130 | 1.5530          | 0.716    |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
