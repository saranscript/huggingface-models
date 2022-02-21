---
language:
- zh-HK
license: apache-2.0
tags:
- automatic-speech-recognition
- common_voice
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the COMMON_VOICE - ZH-HK dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0450
- Wer: 1.8991
- Cer: 0.4717

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 77.5305       | 1.34  | 500   | 92.6669         | 1.0    | 1.0    |
| 9.3568        | 2.68  | 1000  | 7.6860          | 1.0    | 1.0    |
| 6.2735        | 4.02  | 1500  | 6.3664          | 1.0    | 1.0    |
| 6.1322        | 5.36  | 2000  | 6.1999          | 1.0    | 1.0    |
| 6.0244        | 6.7   | 2500  | 6.0719          | 1.0009 | 1.0000 |
| 5.9934        | 8.04  | 3000  | 5.9246          | 1.4023 | 1.0108 |
| 5.807         | 9.38  | 3500  | 5.7572          | 1.8696 | 1.0156 |
| 5.6889        | 10.72 | 4000  | 5.5060          | 1.9285 | 1.0035 |
| 5.4225        | 12.06 | 4500  | 4.9907          | 2.1646 | 1.0005 |
| 4.6644        | 13.4  | 5000  | 3.9605          | 2.0888 | 0.8890 |
| 4.2808        | 14.74 | 5500  | 3.4318          | 2.1360 | 0.8296 |
| 4.1329        | 16.09 | 6000  | 3.1680          | 2.2161 | 0.8428 |
| 3.8779        | 17.43 | 6500  | 2.9402          | 2.2343 | 0.8112 |
| 3.7395        | 18.77 | 7000  | 2.6735          | 2.1611 | 0.7561 |
| 3.5842        | 20.11 | 7500  | 2.3968          | 2.1364 | 0.6983 |
| 3.3861        | 21.45 | 8000  | 2.2187          | 2.1823 | 0.6786 |
| 3.2381        | 22.79 | 8500  | 2.0439          | 2.0273 | 0.6105 |
| 3.1511        | 24.13 | 9000  | 1.9231          | 2.0186 | 0.6136 |
| 3.0449        | 25.47 | 9500  | 1.8028          | 2.1044 | 0.6111 |
| 2.9652        | 26.81 | 10000 | 1.6802          | 2.0883 | 0.5933 |
| 2.8411        | 28.15 | 10500 | 1.5863          | 2.0476 | 0.5600 |
| 2.7381        | 29.49 | 11000 | 1.4835          | 2.0390 | 0.5425 |
| 2.6989        | 30.83 | 11500 | 1.4134          | 2.0879 | 0.5553 |
| 2.6437        | 32.17 | 12000 | 1.3482          | 1.9792 | 0.5212 |
| 2.5781        | 33.51 | 12500 | 1.3063          | 1.9926 | 0.5234 |
| 2.5456        | 34.85 | 13000 | 1.2719          | 1.9736 | 0.5055 |
| 2.489         | 36.19 | 13500 | 1.2196          | 1.9749 | 0.5008 |
| 2.442         | 37.53 | 14000 | 1.1836          | 1.9770 | 0.4999 |
| 2.4021        | 38.87 | 14500 | 1.1609          | 1.9861 | 0.5082 |
| 2.4228        | 40.21 | 15000 | 1.1361          | 1.9359 | 0.4882 |
| 2.3187        | 41.55 | 15500 | 1.1121          | 1.9493 | 0.4926 |
| 2.268         | 42.89 | 16000 | 1.0901          | 1.9346 | 0.4874 |
| 2.27          | 44.24 | 16500 | 1.0758          | 1.9277 | 0.4790 |
| 2.2367        | 45.58 | 17000 | 1.0699          | 1.9298 | 0.4804 |
| 2.2227        | 46.92 | 17500 | 1.0571          | 1.9268 | 0.4792 |
| 2.242         | 48.26 | 18000 | 1.0503          | 1.9078 | 0.4732 |
| 2.1974        | 49.6  | 18500 | 1.0460          | 1.9004 | 0.4724 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
