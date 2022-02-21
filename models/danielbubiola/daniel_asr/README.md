---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: daniel_asr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# daniel_asr

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4565
- Wer: 0.3423

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
| 3.4909        | 4.0   | 500  | 1.3485          | 0.8887 |
| 0.5887        | 8.0   | 1000 | 0.4957          | 0.4641 |
| 0.2207        | 12.0  | 1500 | 0.4621          | 0.3971 |
| 0.125         | 16.0  | 2000 | 0.4339          | 0.3756 |
| 0.0829        | 20.0  | 2500 | 0.4618          | 0.3613 |
| 0.0601        | 24.0  | 3000 | 0.4564          | 0.3535 |
| 0.0456        | 28.0  | 3500 | 0.4565          | 0.3423 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
