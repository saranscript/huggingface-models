---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: t5-large_Run_X3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-large_Run_X3

This model is a fine-tuned version of [t5-large](https://huggingface.co/t5-large) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: nan
- Bleu: 0.4892

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 121
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.33
- training_steps: 500
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu   |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 2.5   | 50   | nan             | 0.5945 |
| No log        | 5.0   | 100  | nan             | 0.5945 |
| No log        | 7.5   | 150  | nan             | 0.5945 |
| No log        | 10.0  | 200  | nan             | 0.5945 |
| No log        | 12.5  | 250  | nan             | 0.5945 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.1+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
