---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: wav2vec2-large-xls-r-300m-sanitycheck
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# wav2vec2-large-xls-r-300m-sanitycheck

This model is a fine-tuned version of [facebook/wav2vec2-xls-r-300m](https://huggingface.co/facebook/wav2vec2-xls-r-300m) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0092
- Accuracy: 1.0

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
- gradient_accumulation_steps: 2
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 12
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.14  | 8    | 0.8034          | 0.4737   |
| No log        | 2.29  | 16   | 0.6803          | 0.5263   |
| No log        | 3.43  | 24   | 0.4867          | 1.0      |
| 0.5907        | 4.57  | 32   | 0.1781          | 0.9474   |
| 0.5907        | 5.71  | 40   | 0.2168          | 0.9474   |
| 0.5907        | 6.86  | 48   | 0.2403          | 0.9474   |
| 0.5907        | 8.0   | 56   | 0.0143          | 1.0      |
| 0.0932        | 9.14  | 64   | 0.0124          | 1.0      |
| 0.0932        | 10.29 | 72   | 0.0089          | 1.0      |
| 0.0932        | 11.43 | 80   | 0.0092          | 1.0      |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
