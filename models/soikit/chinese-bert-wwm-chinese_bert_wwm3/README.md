---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: chinese-bert-wwm-chinese_bert_wwm3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# chinese-bert-wwm-chinese_bert_wwm3

This model is a fine-tuned version of [hfl/chinese-bert-wwm](https://huggingface.co/hfl/chinese-bert-wwm) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0000

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 30.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 72   | 0.4251          |
| No log        | 2.0   | 144  | 0.0282          |
| No log        | 3.0   | 216  | 0.0048          |
| No log        | 4.0   | 288  | 0.0018          |
| No log        | 5.0   | 360  | 0.0011          |
| No log        | 6.0   | 432  | 0.0006          |
| 0.483         | 7.0   | 504  | 0.0004          |
| 0.483         | 8.0   | 576  | 0.0004          |
| 0.483         | 9.0   | 648  | 0.0002          |
| 0.483         | 10.0  | 720  | 0.0002          |
| 0.483         | 11.0  | 792  | 0.0002          |
| 0.483         | 12.0  | 864  | 0.0001          |
| 0.483         | 13.0  | 936  | 0.0001          |
| 0.0031        | 14.0  | 1008 | 0.0001          |
| 0.0031        | 15.0  | 1080 | 0.0001          |
| 0.0031        | 16.0  | 1152 | 0.0001          |
| 0.0031        | 17.0  | 1224 | 0.0001          |
| 0.0031        | 18.0  | 1296 | 0.0001          |
| 0.0031        | 19.0  | 1368 | 0.0001          |
| 0.0031        | 20.0  | 1440 | 0.0001          |
| 0.0015        | 21.0  | 1512 | 0.0001          |
| 0.0015        | 22.0  | 1584 | 0.0001          |
| 0.0015        | 23.0  | 1656 | 0.0001          |
| 0.0015        | 24.0  | 1728 | 0.0001          |
| 0.0015        | 25.0  | 1800 | 0.0000          |
| 0.0015        | 26.0  | 1872 | 0.0001          |
| 0.0015        | 27.0  | 1944 | 0.0000          |
| 0.001         | 28.0  | 2016 | 0.0000          |
| 0.001         | 29.0  | 2088 | 0.0000          |
| 0.001         | 30.0  | 2160 | 0.0000          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.13.3
- Tokenizers 0.10.3
