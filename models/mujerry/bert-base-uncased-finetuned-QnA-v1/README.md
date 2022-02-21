---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased-finetuned-QnA-v1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-QnA-v1

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.7610

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 20

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 39   | 3.3668          |
| No log        | 2.0   | 78   | 3.2134          |
| No log        | 3.0   | 117  | 3.1685          |
| No log        | 4.0   | 156  | 3.1042          |
| No log        | 5.0   | 195  | 3.1136          |
| No log        | 6.0   | 234  | 2.9051          |
| No log        | 7.0   | 273  | 2.9077          |
| No log        | 8.0   | 312  | 2.9774          |
| No log        | 9.0   | 351  | 2.9321          |
| No log        | 10.0  | 390  | 2.9501          |
| No log        | 11.0  | 429  | 2.8544          |
| No log        | 12.0  | 468  | 2.8761          |
| 3.0255        | 13.0  | 507  | 2.8152          |
| 3.0255        | 14.0  | 546  | 2.8046          |
| 3.0255        | 15.0  | 585  | 2.6979          |
| 3.0255        | 16.0  | 624  | 2.6379          |
| 3.0255        | 17.0  | 663  | 2.7091          |
| 3.0255        | 18.0  | 702  | 2.6914          |
| 3.0255        | 19.0  | 741  | 2.7403          |
| 3.0255        | 20.0  | 780  | 2.7479          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
