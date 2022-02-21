---
license: cc-by-nc-sa-4.0
tags:
- generated_from_trainer
model-index:
- name: layoutlmv2-large-uncased-finetuned-vi-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# layoutlmv2-large-uncased-finetuned-vi-infovqa

This model is a fine-tuned version of [microsoft/layoutlmv2-large-uncased](https://huggingface.co/microsoft/layoutlmv2-large-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 8.5806

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
- train_batch_size: 2
- eval_batch_size: 2
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 0.17  | 100  | 4.6181          |
| No log        | 0.33  | 200  | 4.3357          |
| No log        | 0.5   | 300  | 4.3897          |
| No log        | 0.66  | 400  | 4.8238          |
| 4.4277        | 0.83  | 500  | 3.9088          |
| 4.4277        | 0.99  | 600  | 3.6063          |
| 4.4277        | 1.16  | 700  | 3.4278          |
| 4.4277        | 1.32  | 800  | 3.5428          |
| 4.4277        | 1.49  | 900  | 3.4331          |
| 3.0413        | 1.65  | 1000 | 3.3699          |
| 3.0413        | 1.82  | 1100 | 3.3622          |
| 3.0413        | 1.98  | 1200 | 3.5294          |
| 3.0413        | 2.15  | 1300 | 3.7918          |
| 3.0413        | 2.31  | 1400 | 3.4007          |
| 2.0843        | 2.48  | 1500 | 4.0296          |
| 2.0843        | 2.64  | 1600 | 4.1852          |
| 2.0843        | 2.81  | 1700 | 3.6690          |
| 2.0843        | 2.97  | 1800 | 3.6089          |
| 2.0843        | 3.14  | 1900 | 5.5534          |
| 1.7527        | 3.3   | 2000 | 4.7498          |
| 1.7527        | 3.47  | 2100 | 5.2691          |
| 1.7527        | 3.63  | 2200 | 5.1324          |
| 1.7527        | 3.8   | 2300 | 4.5912          |
| 1.7527        | 3.96  | 2400 | 4.1727          |
| 1.2037        | 4.13  | 2500 | 6.1174          |
| 1.2037        | 4.29  | 2600 | 5.7172          |
| 1.2037        | 4.46  | 2700 | 5.8843          |
| 1.2037        | 4.62  | 2800 | 6.4232          |
| 1.2037        | 4.79  | 2900 | 7.4486          |
| 0.8386        | 4.95  | 3000 | 7.1946          |
| 0.8386        | 5.12  | 3100 | 7.9869          |
| 0.8386        | 5.28  | 3200 | 8.0310          |
| 0.8386        | 5.45  | 3300 | 8.2954          |
| 0.8386        | 5.61  | 3400 | 8.5361          |
| 0.4389        | 5.78  | 3500 | 8.6040          |
| 0.4389        | 5.94  | 3600 | 8.5806          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.8.0+cu101
- Datasets 1.17.0
- Tokenizers 0.10.3
