---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: albert-base-v2-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-base-v2-finetuned-squad

This model is a fine-tuned version of [albert-base-v2](https://huggingface.co/albert-base-v2) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1607

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
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.8695        | 1.0   | 5540  | 0.9092          |
| 0.6594        | 2.0   | 11080 | 0.9148          |
| 0.5053        | 3.0   | 16620 | 0.9641          |
| 0.3477        | 4.0   | 22160 | 1.1607          |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
