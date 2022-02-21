---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: output_transformers_3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# output_transformers_3

This model is a fine-tuned version of [distilgpt2](https://huggingface.co/distilgpt2) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.1264

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
- train_batch_size: 1
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2.0
- mixed_precision_training: Native AMP

### Training results



### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.8.0a0+52ea372
- Datasets 1.12.1
- Tokenizers 0.10.3
