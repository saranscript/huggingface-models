---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: MTL-bert-base-uncased
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# MTL-bert-base-uncased

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9283

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
| 2.4409        | 1.0   | 99   | 2.1982          |
| 2.2905        | 2.0   | 198  | 2.1643          |
| 2.1974        | 3.0   | 297  | 2.1168          |
| 2.15          | 4.0   | 396  | 2.0023          |
| 2.0823        | 5.0   | 495  | 2.0199          |
| 2.0752        | 6.0   | 594  | 1.9061          |
| 2.0408        | 7.0   | 693  | 1.9770          |
| 1.9984        | 8.0   | 792  | 1.9322          |
| 1.9933        | 9.0   | 891  | 1.9167          |
| 1.9806        | 10.0  | 990  | 1.9652          |
| 1.9436        | 11.0  | 1089 | 1.9308          |
| 1.9491        | 12.0  | 1188 | 1.9064          |
| 1.929         | 13.0  | 1287 | 1.8831          |
| 1.9096        | 14.0  | 1386 | 1.8927          |
| 1.9032        | 15.0  | 1485 | 1.9117          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
