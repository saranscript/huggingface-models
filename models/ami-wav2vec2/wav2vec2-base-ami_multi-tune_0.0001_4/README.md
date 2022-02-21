---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-base-tune_0.0001_4
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-base-tune_0.0001_4

This model is a fine-tuned version of [facebook/wav2vec2-base](https://huggingface.co/facebook/wav2vec2-base) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5284
- Wer: 0.4735

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.971         | 0.86  | 1000  | 1.8257          | 0.6751 |
| 1.4062        | 1.72  | 2000  | 1.4239          | 0.4815 |
| 1.2763        | 2.59  | 3000  | 1.3776          | 0.4461 |
| 1.2106        | 3.45  | 4000  | 1.3215          | 0.4428 |
| 1.1394        | 4.31  | 5000  | 1.3168          | 0.4343 |
| 1.0651        | 5.17  | 6000  | 1.2975          | 0.4258 |
| 1.0268        | 6.03  | 7000  | 1.3086          | 0.4242 |
| 1.0056        | 6.9   | 8000  | 1.3209          | 0.4295 |
| 0.9655        | 7.76  | 9000  | 1.3159          | 0.4284 |
| 0.9283        | 8.62  | 10000 | 1.3286          | 0.4259 |
| 0.9244        | 9.48  | 11000 | 1.3411          | 0.4243 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
