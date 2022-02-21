---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: distilgpt2-finetuned-AT
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilgpt2-finetuned-AT

This model is a fine-tuned version of [distilgpt2](https://huggingface.co/distilgpt2) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.2450

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 279  | 3.3451          |
| 3.4534        | 2.0   | 558  | 3.2941          |
| 3.4534        | 3.0   | 837  | 3.2740          |
| 3.2435        | 4.0   | 1116 | 3.2617          |
| 3.2435        | 5.0   | 1395 | 3.2556          |
| 3.1729        | 6.0   | 1674 | 3.2490          |
| 3.1729        | 7.0   | 1953 | 3.2475          |
| 3.1262        | 8.0   | 2232 | 3.2467          |
| 3.0972        | 9.0   | 2511 | 3.2448          |
| 3.0972        | 10.0  | 2790 | 3.2450          |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
