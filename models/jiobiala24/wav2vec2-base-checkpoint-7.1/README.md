---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-base-checkpoint-7.1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-checkpoint-7.1

This model is a fine-tuned version of [jiobiala24/wav2vec2-base-checkpoint-6](https://huggingface.co/jiobiala24/wav2vec2-base-checkpoint-6) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9369
- Wer: 0.3243

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
- lr_scheduler_warmup_steps: 1000
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 0.3124        | 1.75  | 1000  | 0.5602          | 0.3403 |
| 0.2428        | 3.5   | 2000  | 0.5924          | 0.3431 |
| 0.1884        | 5.24  | 3000  | 0.6161          | 0.3423 |
| 0.1557        | 6.99  | 4000  | 0.6570          | 0.3415 |
| 0.1298        | 8.74  | 5000  | 0.6837          | 0.3446 |
| 0.1141        | 10.49 | 6000  | 0.7304          | 0.3396 |
| 0.1031        | 12.24 | 7000  | 0.7264          | 0.3410 |
| 0.0916        | 13.99 | 8000  | 0.7229          | 0.3387 |
| 0.0835        | 15.73 | 9000  | 0.8078          | 0.3458 |
| 0.0761        | 17.48 | 10000 | 0.8304          | 0.3408 |
| 0.0693        | 19.23 | 11000 | 0.8290          | 0.3387 |
| 0.0646        | 20.98 | 12000 | 0.8593          | 0.3372 |
| 0.0605        | 22.73 | 13000 | 0.8728          | 0.3345 |
| 0.0576        | 24.48 | 14000 | 0.9111          | 0.3297 |
| 0.0529        | 26.22 | 15000 | 0.9247          | 0.3273 |
| 0.0492        | 27.97 | 16000 | 0.9248          | 0.3250 |
| 0.0472        | 29.72 | 17000 | 0.9369          | 0.3243 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
