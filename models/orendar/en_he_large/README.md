---
language:
- en
- he
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: output_large
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# output_large

This model is a fine-tuned version of [/home/ec2-user/SageMaker/marian_large](https://huggingface.co//home/ec2-user/SageMaker/marian_large) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5473
- Bleu: 32.6637
- Gen Len: 64.8596

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step    | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-------:|:---------------:|:-------:|:-------:|
| 1.7986        | 1.0   | 565689  | 1.8566          | 28.7509 | 66.1132 |
| 1.6695        | 2.0   | 1131378 | 1.7653          | 29.525  | 66.2651 |
| 1.6038        | 3.0   | 1697067 | 1.7081          | 29.8841 | 66.1849 |
| 1.5515        | 4.0   | 2262756 | 1.6601          | 30.588  | 65.9093 |
| 1.5115        | 5.0   | 2828445 | 1.6359          | 30.9726 | 66.2171 |
| 1.474         | 6.0   | 3394134 | 1.6097          | 31.3244 | 66.1843 |
| 1.4425        | 7.0   | 3959823 | 1.5914          | 31.557  | 66.1481 |
| 1.4063        | 8.0   | 4525512 | 1.5666          | 32.0886 | 65.8595 |
| 1.3724        | 9.0   | 5091201 | 1.5537          | 32.3644 | 66.1648 |
| 1.3452        | 10.0  | 5656890 | 1.5473          | 32.4724 | 66.1539 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
