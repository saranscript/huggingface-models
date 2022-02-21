---
license: mit
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: xlm-roberta-large-finetuned-sent_in_news
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-large-finetuned-sent_in_news

This model is a fine-tuned version of [xlm-roberta-large](https://huggingface.co/xlm-roberta-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.8872
- Accuracy: 0.7273
- F1: 0.5125

## Model description

Модель ассиметрична, реагирует на метку X в тексте новости.
Попробуйте следующие примеры:

a) Агентство X понизило рейтинг банка Fitch.                              
b) Агентство Fitch понизило рейтинг банка X.

a) Компания Финам показала рекордную прибыль, говорят аналитики компании X.
b) Компания X показала рекордную прибыль, говорят аналитики компании Финам.

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 10
- eval_batch_size: 10
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 16

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 106  | 1.2526          | 0.6108   | 0.1508 |
| No log        | 2.0   | 212  | 1.1553          | 0.6648   | 0.1141 |
| No log        | 3.0   | 318  | 1.1150          | 0.6591   | 0.1247 |
| No log        | 4.0   | 424  | 1.0007          | 0.6705   | 0.1383 |
| 1.1323        | 5.0   | 530  | 0.9267          | 0.6733   | 0.2027 |
| 1.1323        | 6.0   | 636  | 1.0869          | 0.6335   | 0.4084 |
| 1.1323        | 7.0   | 742  | 1.1224          | 0.6932   | 0.4586 |
| 1.1323        | 8.0   | 848  | 1.2535          | 0.6307   | 0.3424 |
| 1.1323        | 9.0   | 954  | 1.4288          | 0.6932   | 0.4881 |
| 0.5252        | 10.0  | 1060 | 1.5856          | 0.6932   | 0.4739 |
| 0.5252        | 11.0  | 1166 | 1.7101          | 0.6733   | 0.4530 |
| 0.5252        | 12.0  | 1272 | 1.7330          | 0.6903   | 0.4750 |
| 0.5252        | 13.0  | 1378 | 1.8872          | 0.7273   | 0.5125 |
| 0.5252        | 14.0  | 1484 | 1.8797          | 0.7301   | 0.5033 |
| 0.1252        | 15.0  | 1590 | 1.9339          | 0.7330   | 0.5024 |
| 0.1252        | 16.0  | 1696 | 1.9632          | 0.7301   | 0.4967 |


### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
