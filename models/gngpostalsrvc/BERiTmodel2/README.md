---
license: mit
tags:
- generated_from_trainer
model-index:
- name: BERiTmodel2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BERiTmodel2

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.1508

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
| 3.1924        | 1.0   | 2854  | 3.4329          |
| 3.0936        | 2.0   | 5708  | 3.5036          |
| 2.9998        | 3.0   | 8562  | 3.1906          |
| 2.9064        | 4.0   | 11416 | 3.4867          |
| 2.8493        | 5.0   | 14270 | 3.2027          |
| 2.7538        | 6.0   | 17124 | 2.9772          |
| 2.7273        | 7.0   | 19978 | 2.9950          |
| 2.7399        | 8.0   | 22832 | 2.9690          |
| 2.67          | 9.0   | 25686 | 3.0311          |
| 2.6388        | 10.0  | 28540 | 3.1508          |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
