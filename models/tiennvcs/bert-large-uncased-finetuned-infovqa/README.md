---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-large-uncased-finetuned-infovqa
  results:
  - task:
      name: Question Answering
      type: question-answering
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-uncased-finetuned-infovqa

This model is a fine-tuned version of [bert-large-uncased](https://huggingface.co/bert-large-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 6.3170

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 3.7861        | 0.12  | 1000  | 3.2778          |
| 3.2186        | 0.23  | 2000  | 3.0658          |
| 2.8504        | 0.35  | 3000  | 3.0456          |
| 2.8621        | 0.46  | 4000  | 2.8758          |
| 2.7851        | 0.58  | 5000  | 2.8680          |
| 2.8016        | 0.69  | 6000  | 2.9244          |
| 2.7592        | 0.81  | 7000  | 2.7735          |
| 2.5737        | 0.93  | 8000  | 2.7640          |
| 2.3493        | 1.04  | 9000  | 2.7257          |
| 2.1041        | 1.16  | 10000 | 2.8442          |
| 2.1713        | 1.27  | 11000 | 2.7723          |
| 2.0594        | 1.39  | 12000 | 2.9982          |
| 2.1825        | 1.5   | 13000 | 2.8272          |
| 2.2486        | 1.62  | 14000 | 2.8897          |
| 2.097         | 1.74  | 15000 | 2.8557          |
| 2.1645        | 1.85  | 16000 | 2.6342          |
| 2.15          | 1.97  | 17000 | 2.8680          |
| 1.5662        | 2.08  | 18000 | 3.2126          |
| 1.6168        | 2.2   | 19000 | 3.1646          |
| 1.5886        | 2.32  | 20000 | 3.3139          |
| 1.6539        | 2.43  | 21000 | 3.2610          |
| 1.6486        | 2.55  | 22000 | 3.3144          |
| 1.637         | 2.66  | 23000 | 3.0437          |
| 1.7186        | 2.78  | 24000 | 2.9936          |
| 1.7543        | 2.89  | 25000 | 3.1641          |
| 1.5301        | 3.01  | 26000 | 4.0560          |
| 1.1436        | 3.13  | 27000 | 4.0116          |
| 1.1902        | 3.24  | 28000 | 4.0240          |
| 1.2728        | 3.36  | 29000 | 4.3068          |
| 1.2586        | 3.47  | 30000 | 3.7894          |
| 1.3164        | 3.59  | 31000 | 3.9242          |
| 1.3093        | 3.7   | 32000 | 4.0444          |
| 1.2812        | 3.82  | 33000 | 4.1779          |
| 1.3165        | 3.94  | 34000 | 3.6633          |
| 0.8357        | 4.05  | 35000 | 5.8137          |
| 0.9583        | 4.17  | 36000 | 5.3305          |
| 0.9135        | 4.28  | 37000 | 5.4973          |
| 1.0011        | 4.4   | 38000 | 5.0349          |
| 0.9553        | 4.51  | 39000 | 5.2086          |
| 1.0182        | 4.63  | 40000 | 5.1197          |
| 0.9569        | 4.75  | 41000 | 5.4579          |
| 0.9437        | 4.86  | 42000 | 5.4467          |
| 0.9791        | 4.98  | 43000 | 4.7657          |
| 0.648         | 5.09  | 44000 | 6.5780          |
| 0.7528        | 5.21  | 45000 | 6.2827          |
| 0.7247        | 5.33  | 46000 | 6.8500          |
| 0.702         | 5.44  | 47000 | 6.4572          |
| 0.6786        | 5.56  | 48000 | 6.5462          |
| 0.7272        | 5.67  | 49000 | 6.2406          |
| 0.6778        | 5.79  | 50000 | 6.4727          |
| 0.6446        | 5.9   | 51000 | 6.3170          |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.8.0+cu101
- Datasets 1.11.0
- Tokenizers 0.10.3
