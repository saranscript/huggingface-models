---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- super_glue
metrics:
- accuracy
model-index:
- name: bert-base-uncased-finetuned-copa-data-new
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-copa-data-new

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the super_glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5995
- Accuracy: 0.7000

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
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 25   | 0.6564          | 0.6600   |
| No log        | 2.0   | 50   | 0.5995          | 0.7000   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
