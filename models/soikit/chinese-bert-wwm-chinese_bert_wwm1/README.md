---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: chinese-bert-wwm-chinese_bert_wwm1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# chinese-bert-wwm-chinese_bert_wwm1

This model is a fine-tuned version of [hfl/chinese-bert-wwm](https://huggingface.co/hfl/chinese-bert-wwm) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0009

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 30.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 71   | 0.5750          |
| No log        | 2.0   | 142  | 0.0617          |
| No log        | 3.0   | 213  | 0.0109          |
| No log        | 4.0   | 284  | 0.0042          |
| No log        | 5.0   | 355  | 0.0024          |
| No log        | 6.0   | 426  | 0.0017          |
| No log        | 7.0   | 497  | 0.0012          |
| 0.5341        | 8.0   | 568  | 0.0009          |
| 0.5341        | 9.0   | 639  | 0.0009          |
| 0.5341        | 10.0  | 710  | 0.0011          |
| 0.5341        | 11.0  | 781  | 0.0013          |
| 0.5341        | 12.0  | 852  | 0.0012          |
| 0.5341        | 13.0  | 923  | 0.0010          |
| 0.5341        | 14.0  | 994  | 0.0010          |
| 0.0041        | 15.0  | 1065 | 0.0011          |
| 0.0041        | 16.0  | 1136 | 0.0009          |
| 0.0041        | 17.0  | 1207 | 0.0008          |
| 0.0041        | 18.0  | 1278 | 0.0009          |
| 0.0041        | 19.0  | 1349 | 0.0008          |
| 0.0041        | 20.0  | 1420 | 0.0008          |
| 0.0041        | 21.0  | 1491 | 0.0009          |
| 0.0019        | 22.0  | 1562 | 0.0009          |
| 0.0019        | 23.0  | 1633 | 0.0010          |
| 0.0019        | 24.0  | 1704 | 0.0009          |
| 0.0019        | 25.0  | 1775 | 0.0009          |
| 0.0019        | 26.0  | 1846 | 0.0008          |
| 0.0019        | 27.0  | 1917 | 0.0009          |
| 0.0019        | 28.0  | 1988 | 0.0009          |
| 0.0013        | 29.0  | 2059 | 0.0009          |
| 0.0013        | 30.0  | 2130 | 0.0009          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.13.3
- Tokenizers 0.10.3
