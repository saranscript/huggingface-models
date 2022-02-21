---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: MTL-distilbert-base-uncased
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# MTL-distilbert-base-uncased

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0874

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
- train_batch_size: 7
- eval_batch_size: 7
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.5593        | 1.0   | 99   | 2.3163          |
| 2.4346        | 2.0   | 198  | 2.2918          |
| 2.3377        | 3.0   | 297  | 2.2345          |
| 2.2953        | 4.0   | 396  | 2.1463          |
| 2.2296        | 5.0   | 495  | 2.1761          |
| 2.2235        | 6.0   | 594  | 2.0721          |
| 2.1878        | 7.0   | 693  | 2.1460          |
| 2.1569        | 8.0   | 792  | 2.0856          |
| 2.1455        | 9.0   | 891  | 2.1039          |
| 2.1391        | 10.0  | 990  | 2.1112          |
| 2.1056        | 11.0  | 1089 | 2.0694          |
| 2.1076        | 12.0  | 1188 | 2.0501          |
| 2.0919        | 13.0  | 1287 | 2.0484          |
| 2.0669        | 14.0  | 1386 | 2.0342          |
| 2.0595        | 15.0  | 1485 | 2.0802          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
