---
language:
- pa-IN
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

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - PA-IN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6864
- Wer: 0.6707

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 200.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 4.3322        | 14.81  | 400  | 3.7450          | 1.0    |
| 3.2662        | 29.63  | 800  | 3.2571          | 0.9996 |
| 1.6408        | 44.44  | 1200 | 0.9098          | 0.8162 |
| 1.2289        | 59.26  | 1600 | 0.6757          | 0.7099 |
| 1.0551        | 74.07  | 2000 | 0.6417          | 0.7044 |
| 0.966         | 88.89  | 2400 | 0.6365          | 0.6789 |
| 0.8713        | 103.7  | 2800 | 0.6617          | 0.6954 |
| 0.8055        | 118.52 | 3200 | 0.6371          | 0.6762 |
| 0.7489        | 133.33 | 3600 | 0.6798          | 0.6911 |
| 0.7073        | 148.15 | 4000 | 0.6567          | 0.6731 |
| 0.6609        | 162.96 | 4400 | 0.6742          | 0.6840 |
| 0.6435        | 177.78 | 4800 | 0.6862          | 0.6633 |
| 0.6282        | 192.59 | 5200 | 0.6865          | 0.6731 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.4.dev0
- Tokenizers 0.11.0
