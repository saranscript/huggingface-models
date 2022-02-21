---
license: mit
tags:
- generated_from_trainer
datasets:
- conll2003
model_index:
- name: roberta-base-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-ner

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- eval_loss: 0.0814
- eval_precision: 0.9101
- eval_recall: 0.9336
- eval_f1: 0.9217
- eval_accuracy: 0.9799
- eval_runtime: 10.2964
- eval_samples_per_second: 315.646
- eval_steps_per_second: 39.529
- epoch: 1.14
- step: 500

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
- train_batch_size: 32
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4.0

### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
