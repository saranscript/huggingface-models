---
license: mit
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: deberta-base-CoLA
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# deberta-base-CoLA

This model is a fine-tuned version of [microsoft/deberta-base](https://huggingface.co/microsoft/deberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1655
- Accuracy: 0.8482
- F1: 0.8961
- Roc Auc: 0.8987
- Mcc: 0.6288

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.05
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Roc Auc | Mcc    |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:-------:|:------:|
| 0.5266        | 1.0   | 535  | 0.4138          | 0.8159   | 0.8698 | 0.8627  | 0.5576 |
| 0.3523        | 2.0   | 1070 | 0.3852          | 0.8387   | 0.8880 | 0.9041  | 0.6070 |
| 0.2479        | 3.0   | 1605 | 0.3981          | 0.8482   | 0.8901 | 0.9120  | 0.6447 |
| 0.1712        | 4.0   | 2140 | 0.4732          | 0.8558   | 0.9008 | 0.9160  | 0.6486 |
| 0.1354        | 5.0   | 2675 | 0.7181          | 0.8463   | 0.8938 | 0.9024  | 0.6250 |
| 0.0876        | 6.0   | 3210 | 0.8453          | 0.8520   | 0.8992 | 0.9123  | 0.6385 |
| 0.0682        | 7.0   | 3745 | 1.0282          | 0.8444   | 0.8938 | 0.9061  | 0.6189 |
| 0.0431        | 8.0   | 4280 | 1.1114          | 0.8463   | 0.8960 | 0.9010  | 0.6239 |
| 0.0323        | 9.0   | 4815 | 1.1663          | 0.8501   | 0.8970 | 0.8967  | 0.6340 |
| 0.0163        | 10.0  | 5350 | 1.1655          | 0.8482   | 0.8961 | 0.8987  | 0.6288 |


### Framework versions

- Transformers 4.11.0
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
