---
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlmr-base-texas-squad-fr
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlmr-base-texas-squad-fr

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6133

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 2.1478        | 0.23  | 1000  | 1.8543          |
| 1.9827        | 0.46  | 2000  | 1.7643          |
| 1.8427        | 0.69  | 3000  | 1.6789          |
| 1.8372        | 0.92  | 4000  | 1.6137          |
| 1.7318        | 1.15  | 5000  | 1.6093          |
| 1.6603        | 1.38  | 6000  | 1.7157          |
| 1.6334        | 1.61  | 7000  | 1.6302          |
| 1.6716        | 1.84  | 8000  | 1.5845          |
| 1.5192        | 2.06  | 9000  | 1.6690          |
| 1.5174        | 2.29  | 10000 | 1.6669          |
| 1.4611        | 2.52  | 11000 | 1.6301          |
| 1.4648        | 2.75  | 12000 | 1.6009          |
| 1.5052        | 2.98  | 13000 | 1.6133          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
