---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- imdb
model-index:
- name: bert-base-uncased-finetuned-imdb
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
    dataset:
      name: imdb
      type: imdb
      args: plain_text
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-imdb

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the imdb dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0284

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.2244        | 1.0   | 958  | 2.0726          |
| 2.1537        | 2.0   | 1916 | 2.0381          |
| 2.1183        | 3.0   | 2874 | 2.0284          |


### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.1+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
