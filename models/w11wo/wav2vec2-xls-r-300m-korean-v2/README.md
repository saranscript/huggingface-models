---
license: apache-2.0
tags:
- automatic-speech-recognition
- kresnik/zeroth_korean
- generated_from_trainer
datasets:
- zeroth_korean_asr
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the KRESNIK/ZEROTH_KOREAN - CLEAN dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1313
- Wer: 0.2261
- Cer: 0.0899

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 50.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    | Cer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|:------:|
| 5.0816        | 1.44  | 500   | 4.7941          | 1.0    | 1.0    |
| 4.2863        | 2.88  | 1000  | 4.2720          | 0.9961 | 0.9396 |
| 3.3962        | 4.32  | 1500  | 2.4010          | 1.0172 | 0.5761 |
| 2.4739        | 5.76  | 2000  | 1.3089          | 0.8718 | 0.4025 |
| 2.2215        | 7.2   | 2500  | 0.9522          | 0.6912 | 0.2600 |
| 2.0338        | 8.64  | 3000  | 0.8950          | 0.7262 | 0.2943 |
| 1.9666        | 10.09 | 3500  | 0.7557          | 0.6773 | 0.2694 |
| 1.8599        | 11.53 | 4000  | 0.6478          | 0.6161 | 0.2182 |
| 1.7943        | 12.97 | 4500  | 0.6073          | 0.6042 | 0.2170 |
| 1.7241        | 14.41 | 5000  | 0.5658          | 0.5344 | 0.1768 |
| 1.6469        | 15.85 | 5500  | 0.5329          | 0.5388 | 0.1854 |
| 1.5917        | 17.29 | 6000  | 0.5348          | 0.5577 | 0.2048 |
| 1.5364        | 18.73 | 6500  | 0.5058          | 0.5371 | 0.1946 |
| 1.4765        | 20.17 | 7000  | 0.4140          | 0.4248 | 0.1317 |
| 1.3973        | 21.61 | 7500  | 0.3850          | 0.4077 | 0.1183 |
| 1.3456        | 23.05 | 8000  | 0.3349          | 0.4035 | 0.1275 |
| 1.2933        | 24.49 | 8500  | 0.3296          | 0.3612 | 0.1013 |
| 1.2364        | 25.93 | 9000  | 0.3012          | 0.3248 | 0.0902 |
| 1.1763        | 27.38 | 9500  | 0.2968          | 0.3117 | 0.0868 |
| 1.1328        | 28.82 | 10000 | 0.2587          | 0.3096 | 0.0866 |
| 1.0703        | 30.26 | 10500 | 0.2327          | 0.3248 | 0.1120 |
| 1.021         | 31.7  | 11000 | 0.2210          | 0.3345 | 0.1215 |
| 0.9959        | 33.14 | 11500 | 0.2023          | 0.3201 | 0.1151 |
| 0.9495        | 34.58 | 12000 | 0.1985          | 0.2995 | 0.1192 |
| 0.921         | 36.02 | 12500 | 0.1924          | 0.3011 | 0.1218 |
| 0.8567        | 37.46 | 13000 | 0.1758          | 0.2679 | 0.0983 |
| 0.8448        | 38.9  | 13500 | 0.1602          | 0.2662 | 0.1027 |
| 0.8111        | 40.34 | 14000 | 0.1604          | 0.2596 | 0.1015 |
| 0.7823        | 41.78 | 14500 | 0.1475          | 0.2472 | 0.0980 |
| 0.765         | 43.23 | 15000 | 0.1453          | 0.2384 | 0.0939 |
| 0.7375        | 44.67 | 15500 | 0.1406          | 0.2327 | 0.0883 |
| 0.7233        | 46.11 | 16000 | 0.1377          | 0.2295 | 0.0892 |
| 0.6949        | 47.55 | 16500 | 0.1325          | 0.2304 | 0.0917 |
| 0.6838        | 48.99 | 17000 | 0.1321          | 0.2280 | 0.0906 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu102
- Datasets 1.18.2.dev0
- Tokenizers 0.10.3
