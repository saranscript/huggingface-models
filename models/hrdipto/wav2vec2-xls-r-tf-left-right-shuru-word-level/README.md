---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-tf-left-right-shuru-word-level
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-tf-left-right-shuru-word-level

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0504
- Wer: 0.6859

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
- num_epochs: 100
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 23.217        | 23.81 | 500  | 1.3437          | 0.6859 |
| 1.1742        | 47.62 | 1000 | 1.0397          | 0.6859 |
| 1.0339        | 71.43 | 1500 | 1.0155          | 0.6859 |
| 0.9909        | 95.24 | 2000 | 1.0504          | 0.6859 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
