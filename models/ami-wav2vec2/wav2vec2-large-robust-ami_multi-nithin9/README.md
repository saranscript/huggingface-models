---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-robust-ami_multi-nithin9
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-robust-ami_multi-nithin9

This model is a fine-tuned version of [facebook/wav2vec2-large-robust](https://huggingface.co/facebook/wav2vec2-large-robust) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4380
- Wer: 0.4318

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 40.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.3421        | 2.16  | 2500  | 1.2730          | 0.4097 |
| 1.229         | 4.31  | 5000  | 1.2522          | 0.3908 |
| 1.1494        | 6.47  | 7500  | 1.1937          | 0.3857 |
| 1.0801        | 8.62  | 10000 | 1.1936          | 0.3838 |
| 1.0366        | 10.78 | 12500 | 1.1860          | 0.3936 |
| 1.0292        | 12.93 | 15000 | 1.2014          | 0.3819 |
| 0.9217        | 15.09 | 17500 | 1.2313          | 0.3857 |
| 0.9182        | 17.24 | 20000 | 1.2617          | 0.3923 |
| 0.8731        | 19.4  | 22500 | 1.2850          | 0.3940 |
| 0.8471        | 21.55 | 25000 | 1.3432          | 0.3912 |
| 0.8372        | 23.71 | 27500 | 1.3238          | 0.3888 |
| 0.7905        | 25.86 | 30000 | 1.3911          | 0.3962 |
| 0.7553        | 28.02 | 32500 | 1.4314          | 0.3974 |
| 0.7448        | 30.17 | 35000 | 1.4246          | 0.4007 |
| 0.7228        | 32.33 | 37500 | 1.4303          | 0.4006 |
| 0.6941        | 34.48 | 40000 | 1.5059          | 0.4006 |
| 0.6804        | 36.64 | 42500 | 1.5281          | 0.4008 |
| 0.6652        | 38.79 | 45000 | 1.5382          | 0.4004 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
