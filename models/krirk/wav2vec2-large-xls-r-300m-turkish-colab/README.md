---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- common_voice
model-index:
- name: wav2vec2-large-xls-r-300m-turkish-colab
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-turkish-colab

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the common_voice dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3942
- Wer: 0.3149

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 30
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 3.9921        | 3.67  | 400  | 0.7820          | 0.7857 |
| 0.4496        | 7.34  | 800  | 0.4630          | 0.4977 |
| 0.2057        | 11.01 | 1200 | 0.4293          | 0.4627 |
| 0.1328        | 14.68 | 1600 | 0.4464          | 0.4068 |
| 0.1009        | 18.35 | 2000 | 0.4461          | 0.3742 |
| 0.0794        | 22.02 | 2400 | 0.4328          | 0.3467 |
| 0.0628        | 25.69 | 2800 | 0.4036          | 0.3263 |
| 0.0497        | 29.36 | 3200 | 0.3942          | 0.3149 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
