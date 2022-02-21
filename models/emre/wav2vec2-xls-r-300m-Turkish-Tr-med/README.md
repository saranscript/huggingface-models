---
license: apache-2.0
tags:
- generated_from_trainer
- robust-speech-event
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-r-300m-Turkish-Tr-med
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-300m-Turkish-Tr-med

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4727
- Wer: 0.4677

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
- num_epochs: 60
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.8093        | 4.21  | 400  | 2.7831          | 1.0    |
| 0.9881        | 8.42  | 800  | 0.5088          | 0.6681 |
| 0.3519        | 12.63 | 1200 | 0.4496          | 0.6007 |
| 0.2436        | 16.84 | 1600 | 0.4993          | 0.5654 |
| 0.1874        | 21.05 | 2000 | 0.4793          | 0.5530 |
| 0.1561        | 25.26 | 2400 | 0.5187          | 0.5589 |
| 0.1336        | 29.47 | 2800 | 0.5135          | 0.5311 |
| 0.1163        | 33.68 | 3200 | 0.4960          | 0.5143 |
| 0.1056        | 37.89 | 3600 | 0.4795          | 0.5045 |
| 0.0959        | 42.11 | 4000 | 0.4883          | 0.4987 |
| 0.0819        | 46.32 | 4400 | 0.4799          | 0.4903 |
| 0.0756        | 50.53 | 4800 | 0.4822          | 0.4831 |
| 0.0692        | 54.74 | 5200 | 0.4621          | 0.4762 |
| 0.062         | 58.95 | 5600 | 0.4727          | 0.4677 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
