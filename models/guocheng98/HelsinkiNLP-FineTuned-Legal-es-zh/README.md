---
language:
- es
- zh

tags:
- translation

license: apache-2.0
---

This model is a fine-tuned version of [Helsinki-NLP/opus-tatoeba-es-zh](https://huggingface.co/Helsinki-NLP/opus-tatoeba-es-zh) on a dataset of legal domain constructed by the author himself.


# Intended uses & limitations

This model is the result of the master graduation thesis for the Tradumatics: Translation Technologies program at the Autonomous University of Barcelona.

Please refer to the GitHub repo created for this thesis for the full-text and relative open-sourced materials: https://github.com/guocheng98/MUTTT2020_TFM_ZGC

The thesis intends to explain various theories and certain algorithm details about neural machine translation, thus this fine-tuned model only serves as a hands-on practice example for that objective, without any intention of productive usage.


# Training and evaluation data

The dataset is constructed from the Chinese translation of Spanish Civil Code, Spanish Constitution, and many other laws & regulations found in the database China Law Info (北大法宝 Beida Fabao), along with their source text found on Boletín Oficial del Estado and EUR-Lex.

There are 9972 sentence pairs constructed. 1000 are used for evaluation and the rest for training.


# Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 2000
- num_epochs: 10
- mixed_precision_training: Native AMP
- weight_decay: 0.01
- early_stopping_patience: 8


# Training results

Best validation loss achieved at step 5600.

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.9584        | 0.36  | 400  | 2.6800          |
| 2.6402        | 0.71  | 800  | 2.5017          |
| 2.5038        | 1.07  | 1200 | 2.3907          |
| 2.3279        | 1.43  | 1600 | 2.2999          |
| 2.2258        | 1.78  | 2000 | 2.2343          |
| 2.1061        | 2.14  | 2400 | 2.1961          |
| 1.9279        | 2.5   | 2800 | 2.1569          |
| 1.9059        | 2.85  | 3200 | 2.1245          |
| 1.7491        | 3.21  | 3600 | 2.1227          |
| 1.6301        | 3.57  | 4000 | 2.1169          |
| 1.6871        | 3.92  | 4400 | 2.0979          |
| 1.5203        | 4.28  | 4800 | 2.1074          |
| 1.4646        | 4.63  | 5200 | 2.1024          |
| 1.4739        | 4.99  | 5600 | 2.0905          |
| 1.338         | 5.35  | 6000 | 2.0946          |
| 1.3152        | 5.7   | 6400 | 2.0974          |
| 1.306         | 6.06  | 6800 | 2.0985          |
| 1.1991        | 6.42  | 7200 | 2.0962          |
| 1.2113        | 6.77  | 7600 | 2.1092          |
| 1.1983        | 7.13  | 8000 | 2.1060          |
| 1.1238        | 7.49  | 8400 | 2.1102          |
| 1.1417        | 7.84  | 8800 | 2.1078          |


# Framework versions

- Transformers 4.7.0
- Pytorch 1.8.1+cu101
- Datasets 1.8.0
- Tokenizers 0.10.3
