---
license: apache-2.0
tags:
- Finance-sentiment-analysis
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: bert-base-finance-sentiment-noisy-search
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-finance-sentiment-noisy-search

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8400
- Accuracy: 0.8674

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
| 0.4852        | 1.0   | 1022 | 0.4865          | 0.8326   |
| 0.3445        | 2.0   | 2044 | 0.5594          | 0.8478   |
| 0.2096        | 3.0   | 3066 | 0.6503          | 0.8571   |
| 0.097         | 4.0   | 4088 | 0.7111          | 0.8652   |
| 0.0539        | 5.0   | 5110 | 0.8400          | 0.8674   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
