---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: English_ASR
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# English_ASR

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4971
- Wer: 0.3397

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

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.3432        | 4.0   | 500  | 1.1711          | 0.7767 |
| 0.5691        | 8.0   | 1000 | 0.4613          | 0.4357 |
| 0.2182        | 12.0  | 1500 | 0.4715          | 0.3853 |
| 0.1267        | 16.0  | 2000 | 0.4307          | 0.3607 |
| 0.0846        | 20.0  | 2500 | 0.4971          | 0.3537 |
| 0.0608        | 24.0  | 3000 | 0.4712          | 0.3419 |
| 0.0457        | 28.0  | 3500 | 0.4971          | 0.3397 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.13.3
- Tokenizers 0.10.3
