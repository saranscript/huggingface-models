---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: temp
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# temp

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4645
- Wer: 0.3527

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 2
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.4324        | 0.4   | 50   | 0.5800          | 0.4458 |
| 0.4027        | 0.8   | 100  | 0.5374          | 0.4109 |
| 0.3163        | 1.2   | 150  | 0.5285          | 0.3881 |
| 0.3064        | 1.6   | 200  | 0.5161          | 0.3815 |
| 0.3235        | 2.0   | 250  | 0.4645          | 0.3527 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
