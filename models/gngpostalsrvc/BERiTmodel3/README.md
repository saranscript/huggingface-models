---
license: mit
tags:
- generated_from_trainer
model-index:
- name: BERiTmodel3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BERiTmodel3

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.4605

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: cosine
- lr_scheduler_warmup_steps: 280
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 4.1329        | 1.0   | 2854  | 3.9788          |
| 3.8517        | 2.0   | 5708  | 4.0719          |
| 3.6145        | 3.0   | 8562  | 3.6353          |
| 3.4563        | 4.0   | 11416 | 3.8803          |
| 3.364         | 5.0   | 14270 | 3.6327          |
| 3.2525        | 6.0   | 17124 | 3.2436          |
| 3.1732        | 7.0   | 19978 | 3.3924          |
| 3.1542        | 8.0   | 22832 | 3.2765          |
| 3.0772        | 9.0   | 25686 | 3.2873          |
| 3.0236        | 10.0  | 28540 | 3.4605          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
