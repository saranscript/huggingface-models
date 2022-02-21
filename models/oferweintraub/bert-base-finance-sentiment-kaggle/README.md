---
license: apache-2.0
tags:
- sentiment-analysis
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: bert-base-finance-sentiment-kaggle
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-finance-sentiment-kaggle

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2522
- Accuracy: 0.8333

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 455  | 1.1193          | 0.8185   |
| 0.1631        | 2.0   | 910  | 0.9645          | 0.8251   |
| 0.1303        | 3.0   | 1365 | 1.0961          | 0.8119   |
| 0.0455        | 4.0   | 1820 | 1.1955          | 0.8333   |
| 0.0148        | 5.0   | 2275 | 1.2522          | 0.8333   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
