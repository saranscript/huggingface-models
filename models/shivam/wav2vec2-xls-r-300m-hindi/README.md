---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
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

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4031
- Wer: 0.6827

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
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 5.3156        | 3.4   | 500   | 4.5583          | 1.0    |
| 3.3329        | 6.8   | 1000  | 3.4274          | 1.0001 |
| 2.1275        | 10.2  | 1500  | 1.7221          | 0.8763 |
| 1.5737        | 13.6  | 2000  | 1.4188          | 0.8143 |
| 1.3835        | 17.01 | 2500  | 1.2251          | 0.7447 |
| 1.3247        | 20.41 | 3000  | 1.2827          | 0.7394 |
| 1.231         | 23.81 | 3500  | 1.2216          | 0.7074 |
| 1.1819        | 27.21 | 4000  | 1.2210          | 0.6863 |
| 1.1546        | 30.61 | 4500  | 1.3233          | 0.7308 |
| 1.0902        | 34.01 | 5000  | 1.3251          | 0.7010 |
| 1.0749        | 37.41 | 5500  | 1.3274          | 0.7235 |
| 1.0412        | 40.81 | 6000  | 1.2942          | 0.6856 |
| 1.0064        | 44.22 | 6500  | 1.2581          | 0.6732 |
| 1.0006        | 47.62 | 7000  | 1.2767          | 0.6885 |
| 0.9518        | 51.02 | 7500  | 1.2966          | 0.6925 |
| 0.9514        | 54.42 | 8000  | 1.2981          | 0.7067 |
| 0.9241        | 57.82 | 8500  | 1.3835          | 0.7124 |
| 0.9059        | 61.22 | 9000  | 1.3318          | 0.7083 |
| 0.8906        | 64.62 | 9500  | 1.3640          | 0.6962 |
| 0.8468        | 68.03 | 10000 | 1.4727          | 0.6982 |
| 0.8631        | 71.43 | 10500 | 1.3401          | 0.6809 |
| 0.8154        | 74.83 | 11000 | 1.4124          | 0.6955 |
| 0.7953        | 78.23 | 11500 | 1.4245          | 0.6950 |
| 0.818         | 81.63 | 12000 | 1.3944          | 0.6995 |
| 0.7772        | 85.03 | 12500 | 1.3735          | 0.6785 |
| 0.7857        | 88.43 | 13000 | 1.3696          | 0.6808 |
| 0.7705        | 91.84 | 13500 | 1.4101          | 0.6870 |
| 0.7537        | 95.24 | 14000 | 1.4178          | 0.6832 |
| 0.7734        | 98.64 | 14500 | 1.4027          | 0.6831 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu113
- Datasets 1.18.1.dev0
- Tokenizers 0.11.0
