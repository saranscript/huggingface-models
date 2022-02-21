---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
model-index:
- name: layoutlmv2-base-uncased-finetuned-docvqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# layoutlmv2-base-uncased-finetuned-docvqa

This model is a fine-tuned version of [microsoft/layoutlmv2-base-uncased](https://huggingface.co/microsoft/layoutlmv2-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1940

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
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 1.463         | 0.27  | 1000 | 1.6272          |
| 0.9447        | 0.53  | 2000 | 1.3646          |
| 0.7725        | 0.8   | 3000 | 1.2560          |
| 0.5762        | 1.06  | 4000 | 1.3582          |
| 0.4382        | 1.33  | 5000 | 1.2490          |
| 0.4515        | 1.59  | 6000 | 1.1860          |
| 0.383         | 1.86  | 7000 | 1.1940          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.0+cu101
- Datasets 1.14.0
- Tokenizers 0.10.3
