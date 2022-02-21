---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- race
metrics:
- accuracy
model-index:
- name: t5_base_race_cosmos_qa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5_base_race_cosmos_qa

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the race dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4414
- Accuracy: 0.7424

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 100
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.4355        | 1.0   | 10984 | 0.3910          | 0.7072   |
| 0.3233        | 2.0   | 21968 | 0.3833          | 0.7321   |
| 0.229         | 3.0   | 32952 | 0.4414          | 0.7424   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
