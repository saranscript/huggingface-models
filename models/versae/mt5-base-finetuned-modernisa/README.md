---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- bleu
model-index:
- name: mt5-base-finetuned-modernisa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-base-finetuned-modernisa

This model is a fine-tuned version of [google/mt5-base](https://huggingface.co/google/mt5-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3179
- Bleu: 81.9164
- Gen Len: 11.1876

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Bleu    | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|
| 0.4588        | 0.35  | 10000 | 0.4023          | 78.1616 | 11.1577 |
| 0.3982        | 0.71  | 20000 | 0.3584          | 79.3456 | 11.144  |
| 0.3465        | 1.06  | 30000 | 0.3424          | 80.4057 | 11.1625 |
| 0.3236        | 1.42  | 40000 | 0.3349          | 80.9978 | 11.1869 |
| 0.2983        | 1.77  | 50000 | 0.3243          | 81.5426 | 11.1925 |
| 0.278         | 2.13  | 60000 | 0.3210          | 81.794  | 11.2047 |
| 0.2584        | 2.48  | 70000 | 0.3205          | 81.8086 | 11.1986 |
| 0.2609        | 2.84  | 80000 | 0.3179          | 81.9164 | 11.1876 |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.15.2.dev0
- Tokenizers 0.10.3
