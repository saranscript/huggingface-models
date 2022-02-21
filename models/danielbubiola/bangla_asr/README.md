---
tags:
- generated_from_trainer
model-index:
- name: bangla_asr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bangla_asr

This model is a fine-tuned version of [Harveenchadha/vakyansh-wav2vec2-bengali-bnm-200](https://huggingface.co/Harveenchadha/vakyansh-wav2vec2-bengali-bnm-200) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 157.8652
- Wer: 0.4507

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 60
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 2601.5363     | 7.46  | 500  | 259.6630        | 0.6863 |
| 417.7386      | 14.93 | 1000 | 156.6117        | 0.5275 |
| 262.9455      | 22.39 | 1500 | 155.0886        | 0.5006 |
| 178.7715      | 29.85 | 2000 | 155.1077        | 0.4840 |
| 132.448       | 37.31 | 2500 | 163.8623        | 0.4770 |
| 116.3943      | 44.78 | 3000 | 161.5531        | 0.4609 |
| 87.1653       | 52.24 | 3500 | 165.6857        | 0.4597 |
| 80.5606       | 59.7  | 4000 | 157.8652        | 0.4507 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
