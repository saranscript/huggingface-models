---
license: mit
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: xtremedistil-l6-h256-uncased-finetuned_lr-2e-05_epochs-6
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xtremedistil-l6-h256-uncased-finetuned_lr-2e-05_epochs-6

This model is a fine-tuned version of [microsoft/xtremedistil-l6-h256-uncased](https://huggingface.co/microsoft/xtremedistil-l6-h256-uncased) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2578

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
- train_batch_size: 48
- eval_batch_size: 48
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 2.3828        | 1.0   | 1845  | 1.7946          |
| 1.5827        | 2.0   | 3690  | 1.4123          |
| 1.404         | 3.0   | 5535  | 1.3142          |
| 1.346         | 4.0   | 7380  | 1.2819          |
| 1.2871        | 5.0   | 9225  | 1.2630          |
| 1.2538        | 6.0   | 11070 | 1.2578          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
