---
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlm-roberta-base-finetuned-ecoicop
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-base-finetuned-ecoicop

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1685
- Acc: 0.9659

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Acc    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.4224        | 1.0   | 2577  | 0.3612          | 0.9132 |
| 0.2313        | 2.0   | 5154  | 0.2510          | 0.9441 |
| 0.1746        | 3.0   | 7731  | 0.1928          | 0.9569 |
| 0.1325        | 4.0   | 10308 | 0.1731          | 0.9640 |
| 0.0946        | 5.0   | 12885 | 0.1685          | 0.9659 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
