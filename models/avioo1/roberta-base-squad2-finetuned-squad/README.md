---
license: cc-by-4.0
tags:
- generated_from_trainer
model-index:
- name: roberta-base-squad2-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-squad2-finetuned-squad

This model is a fine-tuned version of [deepset/roberta-base-squad2](https://huggingface.co/deepset/roberta-base-squad2) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 5.0220

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 30

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 74   | 1.7148          |
| No log        | 2.0   | 148  | 1.6994          |
| No log        | 3.0   | 222  | 1.7922          |
| No log        | 4.0   | 296  | 1.9947          |
| No log        | 5.0   | 370  | 2.0753          |
| No log        | 6.0   | 444  | 2.2096          |
| 0.9547        | 7.0   | 518  | 2.3070          |
| 0.9547        | 8.0   | 592  | 2.6947          |
| 0.9547        | 9.0   | 666  | 2.7169          |
| 0.9547        | 10.0  | 740  | 2.8503          |
| 0.9547        | 11.0  | 814  | 3.1990          |
| 0.9547        | 12.0  | 888  | 3.4931          |
| 0.9547        | 13.0  | 962  | 3.6575          |
| 0.3191        | 14.0  | 1036 | 3.1863          |
| 0.3191        | 15.0  | 1110 | 3.7922          |
| 0.3191        | 16.0  | 1184 | 3.6336          |
| 0.3191        | 17.0  | 1258 | 4.1156          |
| 0.3191        | 18.0  | 1332 | 4.1353          |
| 0.3191        | 19.0  | 1406 | 3.9888          |
| 0.3191        | 20.0  | 1480 | 4.4290          |
| 0.1904        | 21.0  | 1554 | 4.0473          |
| 0.1904        | 22.0  | 1628 | 4.5048          |
| 0.1904        | 23.0  | 1702 | 4.4026          |
| 0.1904        | 24.0  | 1776 | 4.2864          |
| 0.1904        | 25.0  | 1850 | 4.3941          |
| 0.1904        | 26.0  | 1924 | 4.4921          |
| 0.1904        | 27.0  | 1998 | 4.9139          |
| 0.1342        | 28.0  | 2072 | 4.8914          |
| 0.1342        | 29.0  | 2146 | 5.0148          |
| 0.1342        | 30.0  | 2220 | 5.0220          |


### Framework versions

- Transformers 4.11.0
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
