---
license: mit
tags:
- generated_from_trainer
datasets:
- glue
model-index:
- name: xlnet-base-cased-finetuned-qqp
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlnet-base-cased-finetuned-qqp

This model is a fine-tuned version of [xlnet-base-cased](https://huggingface.co/xlnet-base-cased) on the qqp dataset (part of glue dataset).
It achieves the following results on the evaluation set:
- eval_loss: 0.27
- eval_accuracy: 0.9084
- eval_f1: 0.8775
- epoch: 3

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
- train_batch_size: 16
- eval_batch_size: 16
- weight_decay: 0.01
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
