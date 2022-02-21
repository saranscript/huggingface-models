---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-timit-trainer
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-timit-trainer

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1064
- Wer: 1.0

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.5537        | 4.03  | 500   | 0.6078          | 1.0    |
| 0.5444        | 8.06  | 1000  | 0.4990          | 0.9994 |
| 0.3744        | 12.1  | 1500  | 0.5530          | 1.0    |
| 0.2863        | 16.13 | 2000  | 0.6401          | 1.0    |
| 0.2357        | 20.16 | 2500  | 0.6485          | 1.0    |
| 0.1933        | 24.19 | 3000  | 0.7448          | 0.9994 |
| 0.162         | 28.22 | 3500  | 0.7502          | 1.0    |
| 0.1325        | 32.26 | 4000  | 0.7801          | 1.0    |
| 0.1169        | 36.29 | 4500  | 0.8334          | 1.0    |
| 0.1031        | 40.32 | 5000  | 0.8269          | 1.0    |
| 0.0913        | 44.35 | 5500  | 0.8432          | 1.0    |
| 0.0793        | 48.39 | 6000  | 0.8738          | 1.0    |
| 0.0694        | 52.42 | 6500  | 0.8897          | 1.0    |
| 0.0613        | 56.45 | 7000  | 0.8966          | 1.0    |
| 0.0548        | 60.48 | 7500  | 0.9398          | 1.0    |
| 0.0444        | 64.51 | 8000  | 0.9548          | 1.0    |
| 0.0386        | 68.55 | 8500  | 0.9647          | 1.0    |
| 0.0359        | 72.58 | 9000  | 0.9901          | 1.0    |
| 0.0299        | 76.61 | 9500  | 1.0151          | 1.0    |
| 0.0259        | 80.64 | 10000 | 1.0526          | 1.0    |
| 0.022         | 84.67 | 10500 | 1.0754          | 1.0    |
| 0.0189        | 88.71 | 11000 | 1.0688          | 1.0    |
| 0.0161        | 92.74 | 11500 | 1.0914          | 1.0    |
| 0.0138        | 96.77 | 12000 | 1.1064          | 1.0    |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
