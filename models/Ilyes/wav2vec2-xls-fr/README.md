---
language:
- fr
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-xls-fr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-fr

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - FR dataset.
It achieves the following results on the evaluation set:
- Loss: inf
- Wer: 0.4103

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 128
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 20.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.591         | 1.28  | 500  | inf             | 0.9935 |
| 2.9126        | 2.56  | 1000 | inf             | 0.9935 |
| 1.9567        | 3.84  | 1500 | inf             | 0.8861 |
| 1.4769        | 5.13  | 2000 | inf             | 0.6826 |
| 1.2254        | 6.41  | 2500 | inf             | 0.5388 |
| 1.1349        | 7.69  | 3000 | inf             | 0.4978 |
| 1.0985        | 8.97  | 3500 | inf             | 0.4747 |
| 1.0618        | 10.26 | 4000 | inf             | 0.4578 |
| 1.0258        | 11.54 | 4500 | inf             | 0.4421 |
| 1.0007        | 12.82 | 5000 | inf             | 0.4326 |
| 1.0017        | 14.1  | 5500 | inf             | 0.4263 |
| 0.966         | 15.38 | 6000 | inf             | 0.4216 |
| 0.9604        | 16.67 | 6500 | inf             | 0.4157 |
| 0.9479        | 17.95 | 7000 | inf             | 0.4126 |
| 0.9319        | 19.23 | 7500 | inf             | 0.4106 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
