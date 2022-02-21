---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-base-checkpoint-8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-checkpoint-8

This model is a fine-tuned version of [jiobiala24/wav2vec2-base-checkpoint-7.1](https://huggingface.co/jiobiala24/wav2vec2-base-checkpoint-7.1) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9561
- Wer: 0.3271

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
| 0.3117        | 1.59  | 1000  | 0.5514          | 0.3451 |
| 0.2509        | 3.19  | 2000  | 0.5912          | 0.3328 |
| 0.1918        | 4.78  | 3000  | 0.6103          | 0.3346 |
| 0.1612        | 6.38  | 4000  | 0.6469          | 0.3377 |
| 0.1388        | 7.97  | 5000  | 0.6597          | 0.3391 |
| 0.121         | 9.57  | 6000  | 0.6911          | 0.3472 |
| 0.1096        | 11.16 | 7000  | 0.7300          | 0.3457 |
| 0.0959        | 12.76 | 8000  | 0.7660          | 0.3400 |
| 0.0882        | 14.35 | 9000  | 0.8316          | 0.3394 |
| 0.0816        | 15.95 | 10000 | 0.8042          | 0.3357 |
| 0.0739        | 17.54 | 11000 | 0.8087          | 0.3346 |
| 0.0717        | 19.14 | 12000 | 0.8590          | 0.3353 |
| 0.066         | 20.73 | 13000 | 0.8750          | 0.3336 |
| 0.0629        | 22.33 | 14000 | 0.8759          | 0.3333 |
| 0.0568        | 23.92 | 15000 | 0.8963          | 0.3321 |
| 0.0535        | 25.52 | 16000 | 0.9391          | 0.3323 |
| 0.0509        | 27.11 | 17000 | 0.9279          | 0.3296 |
| 0.0498        | 28.71 | 18000 | 0.9561          | 0.3271 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
