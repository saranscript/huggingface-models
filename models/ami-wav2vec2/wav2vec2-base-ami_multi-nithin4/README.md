---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-ami_multi-nithin4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-ami_multi-nithin4

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0790
- Wer: 0.4478

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 2.8893        | 1.07  | 2500  | 3.7944          | 1.0000 |
| 2.0331        | 2.13  | 5000  | 2.0323          | 0.5840 |
| 1.9009        | 3.2   | 7500  | 1.8876          | 0.5173 |
| 1.8367        | 4.27  | 10000 | 2.1239          | 0.4847 |
| 1.8007        | 5.33  | 12500 | 1.9126          | 0.4684 |
| 1.743         | 6.4   | 15000 | 2.0750          | 0.4570 |
| 1.7329        | 7.47  | 17500 | 1.9226          | 0.4460 |
| 1.7013        | 8.53  | 20000 | 1.9677          | 0.4392 |
| 1.6674        | 9.6   | 22500 | 1.9064          | 0.4360 |
| 1.6568        | 10.67 | 25000 | 1.8144          | 0.4304 |
| 1.6507        | 11.73 | 27500 | 1.8881          | 0.4248 |
| 1.5973        | 12.8  | 30000 | 1.7907          | 0.4267 |
| 1.6316        | 13.87 | 32500 | 1.7567          | 0.4207 |
| 1.6053        | 14.93 | 35000 | 1.7838          | 0.4192 |
| 1.599         | 16.0  | 37500 | 1.8054          | 0.4181 |
| 1.5629        | 17.06 | 40000 | 1.7739          | 0.4135 |
| 1.6124        | 18.13 | 42500 | 2.0690          | 0.4138 |
| 1.5623        | 19.2  | 45000 | 1.9308          | 0.4144 |
| 1.5524        | 20.26 | 47500 | 1.8130          | 0.4121 |
| 1.5654        | 21.33 | 50000 | 1.8344          | 0.4131 |
| 1.5552        | 22.4  | 52500 | 1.9365          | 0.4116 |
| 1.5357        | 23.46 | 55000 | 1.9330          | 0.4114 |
| 1.534         | 24.53 | 57500 | 1.8155          | 0.4079 |
| 1.5333        | 25.6  | 60000 | 1.7895          | 0.4069 |
| 1.5315        | 26.66 | 62500 | 1.7903          | 0.4082 |
| 1.5174        | 27.73 | 65000 | 1.8356          | 0.4080 |
| 1.5209        | 28.8  | 67500 | 1.8147          | 0.4077 |
| 1.5696        | 29.86 | 70000 | 1.8219          | 0.4076 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
