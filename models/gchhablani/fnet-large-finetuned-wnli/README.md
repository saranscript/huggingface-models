---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: fnet-large-finetuned-wnli
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE WNLI
      type: glue
      args: wnli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.38028169014084506
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fnet-large-finetuned-wnli

This model is a fine-tuned version of [google/fnet-large](https://huggingface.co/google/fnet-large) on the GLUE WNLI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6953
- Accuracy: 0.3803

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
- train_batch_size: 4
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.7217        | 1.0   | 159  | 0.6864          | 0.5634   |
| 0.7056        | 2.0   | 318  | 0.6869          | 0.5634   |
| 0.706         | 3.0   | 477  | 0.6875          | 0.5634   |
| 0.7032        | 4.0   | 636  | 0.6931          | 0.5634   |
| 0.7025        | 5.0   | 795  | 0.6953          | 0.3803   |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
