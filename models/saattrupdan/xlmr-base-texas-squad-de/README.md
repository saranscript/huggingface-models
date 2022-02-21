---
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlmr-base-texas-squad-de
  results: []
widget:
- text: "Welche Ausbildung hatte Angela Merkel?"
  context: "Angela Dorothea Merkel (geb. Kasner; * 17. Juli 1954 in Hamburg) ist eine deutsche Politikerin (CDU). Sie war vom 22. November 2005 bis zum 8. Dezember 2021 Bundeskanzlerin der Bundesrepublik Deutschland. Sie ist die achte Person, zugleich erste Frau, erste Person aus Ostdeutschland und erste Person, die nach der Gründung der Bundesrepublik geboren ist, die in dieses Amt gewählt wurde. Von April 2000 bis Dezember 2018 war sie Bundesvorsitzende der CDU. Merkel wuchs in der DDR auf und war dort als Physikerin am Zentralinstitut für Physikalische Chemie tätig. Erstmals politisch aktiv wurde sie während der Wendezeit in der Partei Demokratischer Aufbruch, die sich 1990 der CDU anschloss. In der ersten und gleichzeitig letzten demokratisch gewählten Regierung der DDR übte sie das Amt der stellvertretenden Regierungssprecherin aus."
---

# TExAS-SQuAD-de

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the TExAS-SQuAD-de dataset.
It achieves the following results on the evaluation set:
- Exact match: 61.45%
- F1-score: 66.12%

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.8084        | 1.0   | 4233  | 1.5897          |
| 1.5696        | 2.0   | 8466  | 1.5478          |
| 1.4196        | 3.0   | 12699 | 1.5754          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
