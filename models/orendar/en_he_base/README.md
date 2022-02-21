---
language:
- en
- he
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: output_base
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# output_base

This model is a fine-tuned version of [/home/ec2-user/SageMaker/marian_base](https://huggingface.co//home/ec2-user/SageMaker/marian_base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6852
- Bleu: 30.5903
- Gen Len: 64.8182

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
- train_batch_size: 48
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step    | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-------:|:---------------:|:-------:|:-------:|
| 1.9938        | 1.0   | 188563  | 2.0008          | 27.6169 | 66.0246 |
| 1.8171        | 2.0   | 377126  | 1.8753          | 28.4709 | 65.8859 |
| 1.7389        | 3.0   | 565689  | 1.8120          | 28.9724 | 65.8601 |
| 1.6893        | 4.0   | 754252  | 1.7690          | 29.5248 | 65.8846 |
| 1.6559        | 5.0   | 942815  | 1.7467          | 29.5757 | 65.8046 |
| 1.6279        | 6.0   | 1131378 | 1.7236          | 29.7512 | 66.0482 |
| 1.6053        | 7.0   | 1319941 | 1.7137          | 29.916  | 66.0031 |
| 1.5871        | 8.0   | 1508504 | 1.7007          | 30.1671 | 65.8853 |
| 1.5694        | 9.0   | 1697067 | 1.6921          | 30.3613 | 65.9506 |
| 1.5539        | 10.0  | 1885630 | 1.6852          | 30.4049 | 66.0487 |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
