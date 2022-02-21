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
- Loss: 0.5127
- Wer: 0.3082

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
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.7645        | 2.01  | 500  | 2.5179          | 0.9999 |
| 1.1873        | 4.02  | 1000 | 0.5464          | 0.4798 |
| 0.46          | 6.02  | 1500 | 0.4625          | 0.4025 |
| 0.2869        | 8.03  | 2000 | 0.4252          | 0.3650 |
| 0.2213        | 10.04 | 2500 | 0.4340          | 0.3585 |
| 0.1905        | 12.05 | 3000 | 0.4310          | 0.3404 |
| 0.1545        | 14.06 | 3500 | 0.4547          | 0.3381 |
| 0.1206        | 16.06 | 4000 | 0.4902          | 0.3384 |
| 0.1116        | 18.07 | 4500 | 0.4767          | 0.3253 |
| 0.0925        | 20.08 | 5000 | 0.5248          | 0.3160 |
| 0.0897        | 22.09 | 5500 | 0.4960          | 0.3126 |
| 0.0687        | 24.1  | 6000 | 0.4876          | 0.3086 |
| 0.063         | 26.1  | 6500 | 0.4895          | 0.3065 |
| 0.0558        | 28.11 | 7000 | 0.5127          | 0.3082 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
