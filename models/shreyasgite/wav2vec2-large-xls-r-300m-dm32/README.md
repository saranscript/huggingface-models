---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: wav2vec2-large-xls-r-300m-dm32
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-dm32

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5688
- Accuracy: 0.7917

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 22
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 2.41  | 34   | 0.6769          | 0.6458   |
| No log        | 4.83  | 68   | 0.6864          | 0.5208   |
| No log        | 7.28  | 102  | 0.6596          | 0.6042   |
| 0.7106        | 9.69  | 136  | 0.6208          | 0.6875   |
| 0.7106        | 12.14 | 170  | 0.6152          | 0.6875   |
| 0.7106        | 14.55 | 204  | 0.6167          | 0.6875   |
| 0.6464        | 16.97 | 238  | 0.5782          | 0.7708   |
| 0.6464        | 19.41 | 272  | 0.6011          | 0.7292   |
| 0.6464        | 21.83 | 306  | 0.5688          | 0.7917   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
