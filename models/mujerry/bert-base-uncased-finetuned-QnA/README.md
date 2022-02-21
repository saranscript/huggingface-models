---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model_index:
- name: bert-base-uncased-finetuned-QnA
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-QnA

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0604

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
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 20   | 3.4894          |
| No log        | 2.0   | 40   | 3.5654          |
| No log        | 3.0   | 60   | 3.3185          |
| No log        | 4.0   | 80   | 3.2859          |
| No log        | 5.0   | 100  | 3.2947          |
| No log        | 6.0   | 120  | 3.3998          |
| No log        | 7.0   | 140  | 3.1642          |
| No log        | 8.0   | 160  | 3.2653          |
| No log        | 9.0   | 180  | 3.3427          |
| No log        | 10.0  | 200  | 3.3549          |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.10.2
- Tokenizers 0.10.3
