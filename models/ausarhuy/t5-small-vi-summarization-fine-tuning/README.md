---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: t5-small-vi-summarization-fine-tuning
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-vi-summarization-fine-tuning

This model is a fine-tuned version of [NlpHUST/t5-small-vi-summarization](https://huggingface.co/NlpHUST/t5-small-vi-summarization) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: nan
- Rouge1: 13.0905
- Rouge2: 8.9104
- Rougel: 11.8008
- Rougelsum: 12.1578
- Bleu4: 59.4512

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Bleu4   |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| No log        | 1.0   | 18   | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 2.0   | 36   | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 3.0   | 54   | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 4.0   | 72   | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 5.0   | 90   | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 6.0   | 108  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 7.0   | 126  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 8.0   | 144  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 9.0   | 162  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 10.0  | 180  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 11.0  | 198  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 12.0  | 216  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 13.0  | 234  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 14.0  | 252  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 15.0  | 270  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 16.0  | 288  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 17.0  | 306  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 18.0  | 324  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 19.0  | 342  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |
| No log        | 20.0  | 360  | nan             | 13.0905 | 8.9104 | 11.8008 | 12.1578   | 59.4512 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
