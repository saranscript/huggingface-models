---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: MarianMix_en-10
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# MarianMix_en-10

This model is a fine-tuned version of [Helsinki-NLP/opus-tatoeba-en-ja](https://huggingface.co/Helsinki-NLP/opus-tatoeba-en-ja) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0752
- Bleu: 14.601
- Gen Len: 45.8087

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 32
- seed: 99
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 10
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    | Gen Len  |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:--------:|
| 2.1136        | 0.44  | 500  | 2.0044          | 0.2655  | 109.0201 |
| 1.1422        | 0.89  | 1000 | 1.7516          | 1.4123  | 71.0     |
| 0.9666        | 1.33  | 1500 | 1.5219          | 3.6611  | 64.6888  |
| 0.8725        | 1.78  | 2000 | 1.3606          | 4.6539  | 77.1641  |
| 0.7655        | 2.22  | 2500 | 1.2586          | 8.3456  | 60.3837  |
| 0.7149        | 2.67  | 3000 | 1.1953          | 11.2247 | 50.5921  |
| 0.6719        | 3.11  | 3500 | 1.1541          | 10.4303 | 54.3776  |
| 0.6265        | 3.56  | 4000 | 1.1186          | 13.3231 | 48.283   |
| 0.6157        | 4.0   | 4500 | 1.0929          | 13.8467 | 46.569   |
| 0.5736        | 4.44  | 5000 | 1.0848          | 14.2731 | 45.5035  |
| 0.5683        | 4.89  | 5500 | 1.0752          | 14.601  | 45.8087  |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.9.1
- Datasets 1.17.0
- Tokenizers 0.10.3
