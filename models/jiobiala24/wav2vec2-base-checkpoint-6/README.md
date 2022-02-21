---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-base-checkpoint-6
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-checkpoint-6

This model is a fine-tuned version of [jiobiala24/wav2vec2-base-checkpoint-5](https://huggingface.co/jiobiala24/wav2vec2-base-checkpoint-5) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9738
- Wer: 0.3323

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
| 0.3435        | 1.82  | 1000  | 0.5637          | 0.3419 |
| 0.2599        | 3.65  | 2000  | 0.5804          | 0.3473 |
| 0.2043        | 5.47  | 3000  | 0.6481          | 0.3474 |
| 0.1651        | 7.3   | 4000  | 0.6937          | 0.3452 |
| 0.1376        | 9.12  | 5000  | 0.7221          | 0.3429 |
| 0.118         | 10.95 | 6000  | 0.7634          | 0.3441 |
| 0.105         | 12.77 | 7000  | 0.7789          | 0.3444 |
| 0.0925        | 14.6  | 8000  | 0.8209          | 0.3444 |
| 0.0863        | 16.42 | 9000  | 0.8293          | 0.3440 |
| 0.0756        | 18.25 | 10000 | 0.8553          | 0.3412 |
| 0.0718        | 20.07 | 11000 | 0.9006          | 0.3430 |
| 0.0654        | 21.9  | 12000 | 0.9541          | 0.3458 |
| 0.0605        | 23.72 | 13000 | 0.9400          | 0.3350 |
| 0.0552        | 25.55 | 14000 | 0.9547          | 0.3363 |
| 0.0543        | 27.37 | 15000 | 0.9715          | 0.3348 |
| 0.0493        | 29.2  | 16000 | 0.9738          | 0.3323 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
