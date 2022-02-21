---
language:
- hi
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- robust-speech-event
- generated_from_trainer
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - HI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7346
- Wer: 1.0479

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
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- training_steps: 8000
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 1.36  | 400  | 1.4595          | 1.0039 |
| 4.7778        | 2.71  | 800  | 0.8082          | 1.0115 |
| 0.6408        | 4.07  | 1200 | 0.7032          | 1.0079 |
| 0.3937        | 5.42  | 1600 | 0.6889          | 1.0433 |
| 0.3           | 6.78  | 2000 | 0.6820          | 1.0069 |
| 0.3           | 8.14  | 2400 | 0.6670          | 1.0196 |
| 0.226         | 9.49  | 2800 | 0.7216          | 1.0422 |
| 0.197         | 10.85 | 3200 | 0.7669          | 1.0534 |
| 0.165         | 12.2  | 3600 | 0.7517          | 1.0200 |
| 0.1486        | 13.56 | 4000 | 0.7125          | 1.0357 |
| 0.1486        | 14.92 | 4400 | 0.7447          | 1.0347 |
| 0.122         | 16.27 | 4800 | 0.6899          | 1.0440 |
| 0.1069        | 17.63 | 5200 | 0.7212          | 1.0350 |
| 0.0961        | 18.98 | 5600 | 0.7417          | 1.0408 |
| 0.086         | 20.34 | 6000 | 0.7402          | 1.0356 |
| 0.086         | 21.69 | 6400 | 0.7761          | 1.0420 |
| 0.0756        | 23.05 | 6800 | 0.7346          | 1.0369 |
| 0.0666        | 24.41 | 7200 | 0.7506          | 1.0449 |
| 0.0595        | 25.76 | 7600 | 0.7319          | 1.0476 |
| 0.054         | 27.12 | 8000 | 0.7346          | 1.0479 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
