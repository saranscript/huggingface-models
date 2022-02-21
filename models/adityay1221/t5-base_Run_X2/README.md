---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: t5-base_Run_X2
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-base_Run_X2

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6185
- Bleu: 45.2719

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 121
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.33
- num_epochs: 50
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Bleu    |
|:-------------:|:-----:|:----:|:---------------:|:-------:|
| No log        | 10.0  | 50   | 3.2932          | 2.2530  |
| No log        | 20.0  | 100  | 1.3323          | 15.1192 |
| No log        | 30.0  | 150  | 0.7797          | 43.9378 |
| No log        | 40.0  | 200  | 0.6185          | 46.7000 |
| No log        | 50.0  | 250  | 0.5643          | 46.0571 |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.1+cu102
- Datasets 1.16.1
- Tokenizers 0.10.3
