---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased-issues-128
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-issues-128

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2500

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
- num_epochs: 16

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.0975        | 1.0   | 291  | 1.7060          |
| 1.648         | 2.0   | 582  | 1.4280          |
| 1.4837        | 3.0   | 873  | 1.3980          |
| 1.3978        | 4.0   | 1164 | 1.4040          |
| 1.3314        | 5.0   | 1455 | 1.2032          |
| 1.2954        | 6.0   | 1746 | 1.2814          |
| 1.2448        | 7.0   | 2037 | 1.2635          |
| 1.1983        | 8.0   | 2328 | 1.2071          |
| 1.1849        | 9.0   | 2619 | 1.1675          |
| 1.1414        | 10.0  | 2910 | 1.2095          |
| 1.1314        | 11.0  | 3201 | 1.1858          |
| 1.0943        | 12.0  | 3492 | 1.1658          |
| 1.0838        | 13.0  | 3783 | 1.2336          |
| 1.0733        | 14.0  | 4074 | 1.1606          |
| 1.0627        | 15.0  | 4365 | 1.1188          |
| 1.055         | 16.0  | 4656 | 1.2500          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
