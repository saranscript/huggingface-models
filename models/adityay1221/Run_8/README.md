---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: Run_8
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Run_8

This model is a fine-tuned version of [google/t5-v1_1-large](https://huggingface.co/google/t5-v1_1-large) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: nan
- Bleu: 0.0843

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 7.5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 121
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results



### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0
- Datasets 1.15.1
- Tokenizers 0.10.3
