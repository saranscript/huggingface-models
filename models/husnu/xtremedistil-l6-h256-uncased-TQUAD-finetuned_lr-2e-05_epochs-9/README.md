---
license: mit
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: xtremedistil-l6-h256-uncased-TQUAD-finetuned_lr-2e-05_epochs-9
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xtremedistil-l6-h256-uncased-TQUAD-finetuned_lr-2e-05_epochs-9

This model is a fine-tuned version of [microsoft/xtremedistil-l6-h256-uncased](https://huggingface.co/microsoft/xtremedistil-l6-h256-uncased) on the Turkish squad dataset.
It achieves the following results on the evaluation set:
- Loss: 2.2340

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
- num_epochs: 9

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 3.5236        | 1.0   | 1050 | 3.0042          |
| 2.8489        | 2.0   | 2100 | 2.5866          |
| 2.5485        | 3.0   | 3150 | 2.3526          |
| 2.4067        | 4.0   | 4200 | 2.3535          |
| 2.3091        | 5.0   | 5250 | 2.2862          |
| 2.2401        | 6.0   | 6300 | 2.3989          |
| 2.1715        | 7.0   | 7350 | 2.2284          |
| 2.1414        | 8.0   | 8400 | 2.2298          |
| 2.1221        | 9.0   | 9450 | 2.2340          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
