---
language:
- it
license: apache-2.0
tags:
- automatic-speech-recognition
- robust-speech-event
- mozilla-foundation/common_voice_8_0
- generated_from_trainer
datasets:
- mozilla-foundation/common_voice_8_0
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - SV-SE dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3549
- Wer: 0.3827

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
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.4129        | 5.49  | 500  | 3.3224          | 1.0    |
| 2.9323        | 10.98 | 1000 | 2.9128          | 1.0000 |
| 1.6839        | 16.48 | 1500 | 0.7740          | 0.6854 |
| 1.485         | 21.97 | 2000 | 0.5830          | 0.5976 |
| 1.362         | 27.47 | 2500 | 0.4866          | 0.4905 |
| 1.2752        | 32.96 | 3000 | 0.4240          | 0.4967 |
| 1.1957        | 38.46 | 3500 | 0.3899          | 0.4258 |
| 1.1646        | 43.95 | 4000 | 0.3597          | 0.4014 |
| 1.1265        | 49.45 | 4500 | 0.3559          | 0.3829 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
