---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: wav2vec2-xls-r-timit-tokenizer
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-xls-r-timit-tokenizer

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4285
- Wer: 0.3662

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
| 2.1571        | 4.03  | 500  | 0.5235          | 0.5098 |
| 0.2001        | 8.06  | 1000 | 0.4172          | 0.4375 |
| 0.0968        | 12.1  | 1500 | 0.4562          | 0.4016 |
| 0.0607        | 16.13 | 2000 | 0.4640          | 0.4050 |
| 0.0409        | 20.16 | 2500 | 0.4688          | 0.3914 |
| 0.0273        | 24.19 | 3000 | 0.4414          | 0.3763 |
| 0.0181        | 28.22 | 3500 | 0.4285          | 0.3662 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
