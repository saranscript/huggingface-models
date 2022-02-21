---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-base-checkpoint-10
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-checkpoint-10

This model is a fine-tuned version of [jiobiala24/wav2vec2-base-checkpoint-9](https://huggingface.co/jiobiala24/wav2vec2-base-checkpoint-9) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9567
- Wer: 0.3292

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
| 0.2892        | 1.62  | 1000  | 0.5745          | 0.3467 |
| 0.235         | 3.23  | 2000  | 0.6156          | 0.3423 |
| 0.1782        | 4.85  | 3000  | 0.6299          | 0.3484 |
| 0.1504        | 6.46  | 4000  | 0.6475          | 0.3446 |
| 0.133         | 8.08  | 5000  | 0.6753          | 0.3381 |
| 0.115         | 9.69  | 6000  | 0.7834          | 0.3529 |
| 0.101         | 11.31 | 7000  | 0.7924          | 0.3426 |
| 0.0926        | 12.92 | 8000  | 0.7887          | 0.3465 |
| 0.0863        | 14.54 | 9000  | 0.7674          | 0.3439 |
| 0.0788        | 16.16 | 10000 | 0.8648          | 0.3435 |
| 0.0728        | 17.77 | 11000 | 0.8460          | 0.3395 |
| 0.0693        | 19.39 | 12000 | 0.8941          | 0.3451 |
| 0.0637        | 21.0  | 13000 | 0.9079          | 0.3356 |
| 0.0584        | 22.62 | 14000 | 0.8851          | 0.3336 |
| 0.055         | 24.23 | 15000 | 0.9400          | 0.3338 |
| 0.0536        | 25.85 | 16000 | 0.9387          | 0.3335 |
| 0.0481        | 27.46 | 17000 | 0.9664          | 0.3337 |
| 0.0485        | 29.08 | 18000 | 0.9567          | 0.3292 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
