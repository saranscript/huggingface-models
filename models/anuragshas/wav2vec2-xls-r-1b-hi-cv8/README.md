---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
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

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6780
- Wer: 0.3670

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
- train_batch_size: 8
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2.514         | 2.07  | 400  | 1.4589          | 0.8531 |
| 1.4289        | 4.15  | 800  | 0.8940          | 0.6475 |
| 1.276         | 6.22  | 1200 | 0.7743          | 0.6089 |
| 1.2213        | 8.29  | 1600 | 0.6919          | 0.4973 |
| 1.1522        | 10.36 | 2000 | 0.6635          | 0.4588 |
| 1.0914        | 12.44 | 2400 | 0.6839          | 0.4586 |
| 1.0499        | 14.51 | 2800 | 0.7151          | 0.4467 |
| 1.0238        | 16.58 | 3200 | 0.6824          | 0.4436 |
| 0.9963        | 18.65 | 3600 | 0.6872          | 0.4437 |
| 0.9728        | 20.73 | 4000 | 0.7047          | 0.4244 |
| 0.9373        | 22.8  | 4400 | 0.6569          | 0.4189 |
| 0.9028        | 24.87 | 4800 | 0.6623          | 0.4094 |
| 0.8759        | 26.94 | 5200 | 0.6723          | 0.4152 |
| 0.8824        | 29.02 | 5600 | 0.6467          | 0.4017 |
| 0.8371        | 31.09 | 6000 | 0.6911          | 0.4080 |
| 0.8205        | 33.16 | 6400 | 0.7145          | 0.4063 |
| 0.7837        | 35.23 | 6800 | 0.7037          | 0.3930 |
| 0.7708        | 37.31 | 7200 | 0.6925          | 0.3840 |
| 0.7359        | 39.38 | 7600 | 0.7034          | 0.3829 |
| 0.7153        | 41.45 | 8000 | 0.7030          | 0.3794 |
| 0.7127        | 43.52 | 8400 | 0.6823          | 0.3761 |
| 0.6884        | 45.6  | 8800 | 0.6854          | 0.3711 |
| 0.6835        | 47.67 | 9200 | 0.6723          | 0.3665 |
| 0.6703        | 49.74 | 9600 | 0.6773          | 0.3668 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
