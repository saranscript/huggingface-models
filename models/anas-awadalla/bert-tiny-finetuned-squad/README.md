---
license: mit
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: bert-tiny-finetuned-squad
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-tiny-finetuned-squad

This model is a fine-tuned version of [prajjwal1/bert-tiny](https://huggingface.co/prajjwal1/bert-tiny) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3478

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 20

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 2.7198        | 1.0   | 2767  | 2.5916          |
| 2.6502        | 2.0   | 5534  | 2.5309          |
| 2.5589        | 3.0   | 8301  | 2.4849          |
| 2.5128        | 4.0   | 11068 | 2.4474          |
| 2.4631        | 5.0   | 13835 | 2.4226          |
| 2.4165        | 6.0   | 16602 | 2.3987          |
| 2.3634        | 7.0   | 19369 | 2.4002          |
| 2.3243        | 8.0   | 22136 | 2.3855          |
| 2.2799        | 9.0   | 24903 | 2.3827          |
| 2.2596        | 10.0  | 27670 | 2.3641          |
| 2.2133        | 11.0  | 30437 | 2.3464          |
| 2.1911        | 12.0  | 33204 | 2.3551          |
| 2.1621        | 13.0  | 35971 | 2.3553          |
| 2.1421        | 14.0  | 38738 | 2.3584          |
| 2.1202        | 15.0  | 41505 | 2.3501          |
| 2.1154        | 16.0  | 44272 | 2.3548          |
| 2.1237        | 17.0  | 47039 | 2.3456          |
| 2.0952        | 18.0  | 49806 | 2.3507          |
| 2.0886        | 19.0  | 52573 | 2.3500          |
| 2.1062        | 20.0  | 55340 | 2.3478          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
