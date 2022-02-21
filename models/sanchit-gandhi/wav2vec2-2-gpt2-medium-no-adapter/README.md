---
tags:
- generated_from_trainer
datasets:
- librispeech_asr
model-index:
- name: ''
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# 

This model was trained from scratch on the librispeech_asr dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0860
- Wer: 1.0559

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 5.1263        | 0.28  | 500  | 5.2098          | 1.9557 |
| 4.8677        | 0.56  | 1000 | 5.3297          | 1.9525 |
| 4.6933        | 0.84  | 1500 | 5.0820          | 1.9542 |
| 4.0588        | 1.12  | 2000 | 4.7788          | 1.8837 |
| 3.4627        | 1.4   | 2500 | 3.5971          | 1.7001 |
| 1.7742        | 1.68  | 3000 | 2.1783          | 1.2932 |
| 1.0824        | 1.96  | 3500 | 1.5748          | 1.1542 |
| 0.8691        | 2.24  | 4000 | 1.3047          | 1.0996 |
| 0.4536        | 2.52  | 4500 | 1.1965          | 1.0699 |
| 0.4566        | 2.8   | 5000 | 1.0860          | 1.0559 |


### Framework versions

- Transformers 4.17.0.dev0
- Pytorch 1.10.2+cu113
- Datasets 1.18.3
- Tokenizers 0.11.0
