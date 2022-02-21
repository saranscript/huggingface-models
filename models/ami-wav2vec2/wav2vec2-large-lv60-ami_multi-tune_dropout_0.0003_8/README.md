---
language:
- en
license: apache-2.0
tags:
- automatic-speech-recognition
- ami
- generated_from_trainer
model-index:
- name: wav2vec2-large-lv60-ami_multi-tune_dropout_0.0003_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-lv60-ami_multi-tune_dropout_0.0003_8

This model is a fine-tuned version of [facebook/wav2vec2-large-lv60](https://huggingface.co/facebook/wav2vec2-large-lv60) on the AMI-IHM dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4292
- Wer: 0.4203

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
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Wer    |
|:-------------:|:-----:|:-----:|:---------------:|:------:|
| 1.6596        | 0.86  | 1000  | 1.4908          | 0.5105 |
| 1.4211        | 1.72  | 2000  | 1.3459          | 0.4167 |
| 1.3246        | 2.59  | 3000  | 1.2844          | 0.3992 |
| 1.2588        | 3.45  | 4000  | 1.2392          | 0.3995 |
| 1.2045        | 4.31  | 5000  | 1.2349          | 0.3928 |
| 1.1543        | 5.17  | 6000  | 1.2056          | 0.3886 |
| 1.119         | 6.03  | 7000  | 1.2005          | 0.3793 |
| 1.0984        | 6.9   | 8000  | 1.2024          | 0.3808 |
| 1.0726        | 7.76  | 9000  | 1.1921          | 0.3791 |
| 1.054         | 8.62  | 10000 | 1.1835          | 0.3793 |
| 1.0498        | 9.48  | 11000 | 1.1854          | 0.3743 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1
- Datasets 1.12.2.dev0
- Tokenizers 0.10.3
