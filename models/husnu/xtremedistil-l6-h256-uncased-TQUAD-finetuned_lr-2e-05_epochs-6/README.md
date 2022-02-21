---
license: mit
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: xtremedistil-l6-h256-uncased-TQUAD-finetuned_lr-2e-05_epochs-6
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xtremedistil-l6-h256-uncased-TQUAD-finetuned_lr-2e-05_epochs-6

This model is a fine-tuned version of [microsoft/xtremedistil-l6-h256-uncased](https://huggingface.co/microsoft/xtremedistil-l6-h256-uncased) on the Turkish squad dataset.
It achieves the following results on the evaluation set:
- Loss: 2.8135

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

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 350  | 3.8389          |
| 4.4474        | 2.0   | 700  | 3.3748          |
| 3.512         | 3.0   | 1050 | 3.0657          |
| 3.512         | 4.0   | 1400 | 2.9219          |
| 3.1526        | 5.0   | 1750 | 2.8517          |
| 2.9972        | 6.0   | 2100 | 2.8135          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
