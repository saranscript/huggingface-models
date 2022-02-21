---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-yahd
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-yahd

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 5.7685
- Accuracy: 0.4010

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 16

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Accuracy |
|:-------------:|:-----:|:------:|:---------------:|:--------:|
| 2.2439        | 1.0   | 9142   | 2.1898          | 0.2130   |
| 1.9235        | 2.0   | 18284  | 2.1045          | 0.2372   |
| 1.5915        | 3.0   | 27426  | 2.1380          | 0.2550   |
| 1.3262        | 4.0   | 36568  | 2.2544          | 0.2758   |
| 1.0529        | 5.0   | 45710  | 2.5662          | 0.2955   |
| 0.8495        | 6.0   | 54852  | 2.8731          | 0.3078   |
| 0.6779        | 7.0   | 63994  | 3.1980          | 0.3218   |
| 0.5546        | 8.0   | 73136  | 3.6289          | 0.3380   |
| 0.4738        | 9.0   | 82278  | 3.9732          | 0.3448   |
| 0.412         | 10.0  | 91420  | 4.2945          | 0.3565   |
| 0.3961        | 11.0  | 100562 | 4.6127          | 0.3772   |
| 0.3292        | 12.0  | 109704 | 4.9586          | 0.3805   |
| 0.318         | 13.0  | 118846 | 5.2615          | 0.3887   |
| 0.2936        | 14.0  | 127988 | 5.4567          | 0.3931   |
| 0.2671        | 15.0  | 137130 | 5.6902          | 0.3965   |
| 0.2301        | 16.0  | 146272 | 5.7685          | 0.4010   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
