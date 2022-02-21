---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: Prototype_training
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# Prototype_training

This model is a fine-tuned version of [scasutt/Prototype_training](https://huggingface.co/scasutt/Prototype_training) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3719
- Wer: 0.4626

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 2
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Wer    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.3853        | 1.47  | 100  | 0.3719          | 0.4626 |
| 0.3867        | 2.94  | 200  | 0.3719          | 0.4626 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
