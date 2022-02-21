---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-irish-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-irish-colab

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4286
- Wer: 0.5097

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
- train_batch_size: 32
- eval_batch_size: 16
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 64
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 210
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch  | Step | Validation Loss | Wer    |
|:-------------:|:------:|:----:|:---------------:|:------:|
| 4.3406        | 24.97  | 400  | 1.1677          | 0.7270 |
| 0.2527        | 49.97  | 800  | 1.2686          | 0.5927 |
| 0.0797        | 74.97  | 1200 | 1.3970          | 0.5769 |
| 0.0424        | 99.97  | 1600 | 1.4093          | 0.5600 |
| 0.0286        | 124.97 | 2000 | 1.3684          | 0.5407 |
| 0.0174        | 149.97 | 2400 | 1.4571          | 0.5205 |
| 0.0109        | 174.97 | 2800 | 1.4327          | 0.5178 |
| 0.0072        | 199.97 | 3200 | 1.4286          | 0.5097 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu113
- Datasets 1.13.3
- Tokenizers 0.10.3
