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
- Loss: 0.7805
- Wer: 0.4340

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
| No log        | 1.36  | 400  | 1.9130          | 0.9244 |
| 5.0013        | 2.71  | 800  | 0.7789          | 0.5944 |
| 0.6544        | 4.07  | 1200 | 0.7298          | 0.5852 |
| 0.4021        | 5.42  | 1600 | 0.6978          | 0.5667 |
| 0.3003        | 6.78  | 2000 | 0.6764          | 0.5382 |
| 0.3003        | 8.14  | 2400 | 0.7249          | 0.5463 |
| 0.2345        | 9.49  | 2800 | 0.7280          | 0.5124 |
| 0.1993        | 10.85 | 3200 | 0.7289          | 0.4690 |
| 0.1617        | 12.2  | 3600 | 0.7431          | 0.4733 |
| 0.1432        | 13.56 | 4000 | 0.7448          | 0.4733 |
| 0.1432        | 14.92 | 4400 | 0.7746          | 0.4485 |
| 0.1172        | 16.27 | 4800 | 0.7589          | 0.4742 |
| 0.1035        | 17.63 | 5200 | 0.7539          | 0.4353 |
| 0.0956        | 18.98 | 5600 | 0.7648          | 0.4495 |
| 0.0845        | 20.34 | 6000 | 0.7877          | 0.4719 |
| 0.0845        | 21.69 | 6400 | 0.7884          | 0.4434 |
| 0.0761        | 23.05 | 6800 | 0.7796          | 0.4386 |
| 0.0634        | 24.41 | 7200 | 0.7729          | 0.4306 |
| 0.0571        | 25.76 | 7600 | 0.7826          | 0.4298 |
| 0.0508        | 27.12 | 8000 | 0.7805          | 0.4340 |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
