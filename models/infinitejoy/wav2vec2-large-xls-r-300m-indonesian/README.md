---
language:
- id
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-indonesian
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-indonesian

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - ID dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2759
- Wer: 0.3256

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7e-05
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 4000
- num_epochs: 100.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 3.0387        | 4.72  | 1000  | 3.0892          | 1.0    |
| 1.7911        | 9.43  | 2000  | 0.8451          | 0.6702 |
| 1.2826        | 14.15 | 3000  | 0.4211          | 0.4166 |
| 1.1802        | 18.87 | 4000  | 0.3508          | 0.4690 |
| 1.1065        | 23.58 | 5000  | 0.3319          | 0.4662 |
| 1.0921        | 28.3  | 6000  | 0.3056          | 0.3880 |
| 1.0366        | 33.02 | 7000  | 0.2997          | 0.3665 |
| 0.9988        | 37.74 | 8000  | 0.2972          | 0.3653 |
| 0.9864        | 42.45 | 9000  | 0.2697          | 0.3371 |
| 0.9558        | 47.17 | 10000 | 0.2739          | 0.3141 |
| 0.9094        | 51.89 | 11000 | 0.2657          | 0.3533 |
| 0.9034        | 56.6  | 12000 | 0.2699          | 0.3397 |
| 0.8907        | 61.32 | 13000 | 0.2765          | 0.3470 |
| 0.8631        | 66.04 | 14000 | 0.2774          | 0.3346 |
| 0.8389        | 70.75 | 15000 | 0.2743          | 0.3365 |
| 0.8214        | 75.47 | 16000 | 0.2778          | 0.3201 |
| 0.8195        | 80.19 | 17000 | 0.2725          | 0.3286 |
| 0.7994        | 84.91 | 18000 | 0.2782          | 0.3315 |
| 0.7816        | 89.62 | 19000 | 0.2775          | 0.3363 |
| 0.7816        | 94.34 | 20000 | 0.2731          | 0.3278 |
| 0.7635        | 99.06 | 21000 | 0.2767          | 0.3259 |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.1+cu102
- Datasets 1.17.1.dev0
- Tokenizers 0.11.0
