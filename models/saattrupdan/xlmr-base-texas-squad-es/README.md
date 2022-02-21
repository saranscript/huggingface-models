---
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlmr-base-texas-squad-es
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlmr-base-texas-squad-es

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5504

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
| 2.0645        | 0.24  | 1000  | 1.7915          |
| 1.8458        | 0.47  | 2000  | 1.7873          |
| 1.8208        | 0.71  | 3000  | 1.6628          |
| 1.7743        | 0.95  | 4000  | 1.5684          |
| 1.5636        | 1.18  | 5000  | 1.5686          |
| 1.6017        | 1.42  | 6000  | 1.5484          |
| 1.6271        | 1.66  | 7000  | 1.5173          |
| 1.5975        | 1.89  | 8000  | 1.5209          |
| 1.477         | 2.13  | 9000  | 1.5766          |
| 1.4389        | 2.37  | 10000 | 1.5392          |
| 1.3389        | 2.6   | 11000 | 1.5298          |
| 1.437         | 2.84  | 12000 | 1.5504          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.1+cu101
- Datasets 1.12.1
- Tokenizers 0.10.3
