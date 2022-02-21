---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: distilbert-base-uncased-finetuned-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-infovqa

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.8872

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 0.02  | 100  | 4.7706          |
| No log        | 0.05  | 200  | 4.4399          |
| No log        | 0.07  | 300  | 3.8175          |
| No log        | 0.09  | 400  | 3.8306          |
| 3.3071        | 0.12  | 500  | 3.6480          |
| 3.3071        | 0.14  | 600  | 3.6451          |
| 3.3071        | 0.16  | 700  | 3.4974          |
| 3.3071        | 0.19  | 800  | 3.4686          |
| 3.3071        | 0.21  | 900  | 3.4703          |
| 3.5336        | 0.23  | 1000 | 3.3165          |
| 3.5336        | 0.25  | 1100 | 3.3634          |
| 3.5336        | 0.28  | 1200 | 3.3466          |
| 3.5336        | 0.3   | 1300 | 3.3411          |
| 3.5336        | 0.32  | 1400 | 3.2456          |
| 3.3593        | 0.35  | 1500 | 3.3257          |
| 3.3593        | 0.37  | 1600 | 3.2941          |
| 3.3593        | 0.39  | 1700 | 3.2581          |
| 3.3593        | 0.42  | 1800 | 3.1680          |
| 3.3593        | 0.44  | 1900 | 3.2077          |
| 3.2436        | 0.46  | 2000 | 3.2422          |
| 3.2436        | 0.49  | 2100 | 3.2529          |
| 3.2436        | 0.51  | 2200 | 3.2681          |
| 3.2436        | 0.53  | 2300 | 3.1055          |
| 3.2436        | 0.56  | 2400 | 3.0174          |
| 3.093         | 0.58  | 2500 | 3.0608          |
| 3.093         | 0.6   | 2600 | 3.0200          |
| 3.093         | 0.63  | 2700 | 2.9884          |
| 3.093         | 0.65  | 2800 | 3.0041          |
| 3.093         | 0.67  | 2900 | 2.9700          |
| 3.0087        | 0.69  | 3000 | 3.0993          |
| 3.0087        | 0.72  | 3100 | 3.0499          |
| 3.0087        | 0.74  | 3200 | 2.9317          |
| 3.0087        | 0.76  | 3300 | 3.0817          |
| 3.0087        | 0.79  | 3400 | 3.0035          |
| 2.9694        | 0.81  | 3500 | 3.0850          |
| 2.9694        | 0.83  | 3600 | 2.9948          |
| 2.9694        | 0.86  | 3700 | 2.9874          |
| 2.9694        | 0.88  | 3800 | 2.9202          |
| 2.9694        | 0.9   | 3900 | 2.9322          |
| 2.8277        | 0.93  | 4000 | 2.9195          |
| 2.8277        | 0.95  | 4100 | 2.8638          |
| 2.8277        | 0.97  | 4200 | 2.8809          |
| 2.8277        | 1.0   | 4300 | 2.8872          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
