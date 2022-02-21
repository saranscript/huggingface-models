---
tags:
- generated_from_trainer
model-index:
- name: bertweet-base-SNS_BRANDS_50k
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bertweet-base-SNS_BRANDS_50k

This model is a fine-tuned version of [vinai/bertweet-base](https://huggingface.co/vinai/bertweet-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0490

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
- lr_scheduler_warmup_steps: 500
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.0787        | 1.0   | 1465 | 0.0751          |
| 0.0662        | 2.0   | 2930 | 0.0628          |
| 0.053         | 3.0   | 4395 | 0.0531          |
| 0.0452        | 4.0   | 5860 | 0.0490          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
