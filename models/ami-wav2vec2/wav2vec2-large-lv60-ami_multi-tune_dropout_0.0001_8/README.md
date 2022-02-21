---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-tune_dropout_0.0001_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-tune_dropout_0.0001_8

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4880
- Wer: 0.4295

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.8417        | 0.86  | 1000  | 2.6883          | 0.9997 |
| 1.5626        | 1.72  | 2000  | 1.4253          | 0.4517 |
| 1.4476        | 2.59  | 3000  | 1.3356          | 0.4157 |
| 1.3874        | 3.45  | 4000  | 1.2814          | 0.4073 |
| 1.3391        | 4.31  | 5000  | 1.2700          | 0.4044 |
| 1.2983        | 5.17  | 6000  | 1.2423          | 0.3967 |
| 1.2618        | 6.03  | 7000  | 1.2429          | 0.3879 |
| 1.2414        | 6.9   | 8000  | 1.2290          | 0.3878 |
| 1.2286        | 7.76  | 9000  | 1.2301          | 0.3882 |
| 1.2254        | 8.62  | 10000 | 1.2140          | 0.3885 |
| 1.2257        | 9.48  | 11000 | 1.2154          | 0.3840 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
