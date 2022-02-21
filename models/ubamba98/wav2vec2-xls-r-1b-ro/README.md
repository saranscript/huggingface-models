---
language:
- ro
license: apache-2.0
tags:
- automatic-speech-recognition
- mozilla-foundation/common_voice_7_0
- generated_from_trainer
- robust-speech-event
datasets:
- mozilla-foundation/common_voice_7_0
model-index:
- name: wav2vec2-xls-r-1b-ro
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-1b-ro

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-1b](https://huggingface.co/facebook/wav2vec2-xls-r-1b) on the MOZILLA-FOUNDATION/COMMON_VOICE_7_0 - RO dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1113
- Wer: 0.4770
- Cer: 0.0306

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 0.7844        | 1.67  | 1500  | 0.3412          | 0.8600 | 0.0940 |
| 0.7272        | 3.34  | 3000  | 0.1926          | 0.6409 | 0.0527 |
| 0.6924        | 5.02  | 4500  | 0.1413          | 0.5722 | 0.0401 |
| 0.6327        | 6.69  | 6000  | 0.1252          | 0.5366 | 0.0371 |
| 0.6363        | 8.36  | 7500  | 0.1235          | 0.5741 | 0.0389 |
| 0.6238        | 10.03 | 9000  | 0.1180          | 0.5542 | 0.0362 |
| 0.6018        | 11.71 | 10500 | 0.1192          | 0.5694 | 0.0369 |
| 0.583         | 13.38 | 12000 | 0.1216          | 0.5772 | 0.0385 |
| 0.5643        | 15.05 | 13500 | 0.1195          | 0.5419 | 0.0371 |
| 0.5399        | 16.72 | 15000 | 0.1240          | 0.5224 | 0.0370 |
| 0.5529        | 18.39 | 16500 | 0.1174          | 0.5555 | 0.0367 |
| 0.5246        | 20.07 | 18000 | 0.1097          | 0.5047 | 0.0339 |
| 0.4936        | 21.74 | 19500 | 0.1225          | 0.5189 | 0.0382 |
| 0.4629        | 23.41 | 21000 | 0.1142          | 0.5047 | 0.0344 |
| 0.4463        | 25.08 | 22500 | 0.1168          | 0.4887 | 0.0339 |
| 0.4671        | 26.76 | 24000 | 0.1119          | 0.5073 | 0.0338 |
| 0.4359        | 28.43 | 25500 | 0.1206          | 0.5479 | 0.0363 |
| 0.4225        | 30.1  | 27000 | 0.1122          | 0.5170 | 0.0345 |
| 0.4038        | 31.77 | 28500 | 0.1159          | 0.5032 | 0.0343 |
| 0.4271        | 33.44 | 30000 | 0.1116          | 0.5126 | 0.0339 |
| 0.3867        | 35.12 | 31500 | 0.1101          | 0.4937 | 0.0327 |
| 0.3674        | 36.79 | 33000 | 0.1142          | 0.4940 | 0.0330 |
| 0.3607        | 38.46 | 34500 | 0.1106          | 0.5145 | 0.0327 |
| 0.3651        | 40.13 | 36000 | 0.1172          | 0.4921 | 0.0317 |
| 0.3268        | 41.81 | 37500 | 0.1093          | 0.4830 | 0.0310 |
| 0.3345        | 43.48 | 39000 | 0.1131          | 0.4760 | 0.0314 |
| 0.3236        | 45.15 | 40500 | 0.1132          | 0.4864 | 0.0317 |
| 0.312         | 46.82 | 42000 | 0.1124          | 0.4861 | 0.0315 |
| 0.3106        | 48.49 | 43500 | 0.1116          | 0.4745 | 0.0306 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.11.0
