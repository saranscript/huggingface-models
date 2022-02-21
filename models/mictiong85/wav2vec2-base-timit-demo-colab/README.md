---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-base-timit-demo-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-timit-demo-colab

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4635
- Wer: 0.3357

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
| 3.6808        | 4.0   | 500  | 1.5478          | 1.0481 |
| 0.835         | 8.0   | 1000 | 0.4611          | 0.4703 |
| 0.3013        | 12.0  | 1500 | 0.4327          | 0.3887 |
| 0.1741        | 16.0  | 2000 | 0.4073          | 0.3677 |
| 0.1309        | 20.0  | 2500 | 0.4306          | 0.3595 |
| 0.1097        | 24.0  | 3000 | 0.4318          | 0.3475 |
| 0.0825        | 28.0  | 3500 | 0.4635          | 0.3357 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
