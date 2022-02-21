---
language:
- ja
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

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_8_0 - JA dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9566
- Wer: 1.2002

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
- train_batch_size: 32
- eval_batch_size: 2
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.6322        | 6.02  | 1000 | 2.6345          | 1.4956 |
| 1.867         | 12.05 | 2000 | 1.2855          | 1.1065 |
| 1.3979        | 18.07 | 3000 | 1.0691          | 0.9978 |
| 1.1066        | 24.1  | 4000 | 1.0317          | 1.0534 |
| 0.891         | 30.12 | 5000 | 0.9662          | 1.1817 |
| 0.7455        | 36.14 | 6000 | 0.9614          | 1.2226 |
| 0.6349        | 42.17 | 7000 | 0.9685          | 1.2324 |
| 0.5616        | 48.19 | 8000 | 0.9608          | 1.2064 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.18.3
- Tokenizers 0.11.0
