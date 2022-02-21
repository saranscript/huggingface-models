---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased-finetuned-docvqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-docvqa

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9146

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 2.2151        | 0.1   | 1000  | 2.6299          |
| 1.8885        | 0.21  | 2000  | 2.2217          |
| 1.7353        | 0.31  | 3000  | 2.1675          |
| 1.6188        | 0.41  | 4000  | 2.2436          |
| 1.5802        | 0.52  | 5000  | 2.0539          |
| 1.4875        | 0.62  | 6000  | 2.0551          |
| 1.4675        | 0.73  | 7000  | 1.9368          |
| 1.3485        | 0.83  | 8000  | 1.9456          |
| 1.3273        | 0.93  | 9000  | 1.9281          |
| 1.1048        | 1.04  | 10000 | 1.9333          |
| 0.9529        | 1.14  | 11000 | 2.2019          |
| 0.9418        | 1.24  | 12000 | 2.0381          |
| 0.9209        | 1.35  | 13000 | 1.8753          |
| 0.8788        | 1.45  | 14000 | 1.9964          |
| 0.8729        | 1.56  | 15000 | 1.9690          |
| 0.8671        | 1.66  | 16000 | 1.8513          |
| 0.8379        | 1.76  | 17000 | 1.9627          |
| 0.8722        | 1.87  | 18000 | 1.8988          |
| 0.7842        | 1.97  | 19000 | 1.9146          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
