---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-lv-v05
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-lv-v05

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3862
- Wer: 0.2588

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
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 4.8836        | 2.81  | 400  | 0.8722          | 0.7244 |
| 0.5365        | 5.63  | 800  | 0.4622          | 0.4812 |
| 0.277         | 8.45  | 1200 | 0.4348          | 0.4056 |
| 0.1947        | 11.27 | 1600 | 0.4223          | 0.3636 |
| 0.1655        | 14.08 | 2000 | 0.4084          | 0.3465 |
| 0.1441        | 16.9  | 2400 | 0.4329          | 0.3497 |
| 0.121         | 19.72 | 2800 | 0.4371          | 0.3324 |
| 0.1062        | 22.53 | 3200 | 0.4202          | 0.3198 |
| 0.0937        | 25.35 | 3600 | 0.4063          | 0.3265 |
| 0.0871        | 28.17 | 4000 | 0.4253          | 0.3255 |
| 0.0755        | 30.98 | 4400 | 0.4368          | 0.3194 |
| 0.0627        | 33.8  | 4800 | 0.4067          | 0.2908 |
| 0.0595        | 36.62 | 5200 | 0.3929          | 0.2973 |
| 0.0523        | 39.44 | 5600 | 0.3748          | 0.2817 |
| 0.0434        | 42.25 | 6000 | 0.3769          | 0.2711 |
| 0.0391        | 45.07 | 6400 | 0.3901          | 0.2653 |
| 0.0319        | 47.88 | 6800 | 0.3862          | 0.2588 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
