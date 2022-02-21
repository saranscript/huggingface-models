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
- name: albert-base-v2_mnli_bc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE MNLI
      type: glue
      args: mnli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9398776667163956
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-base-v2_mnli_bc

This model is a fine-tuned version of [albert-base-v2](https://huggingface.co/albert-base-v2) on the GLUE MNLI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2952
- Accuracy: 0.9399

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
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.2159        | 1.0   | 16363 | 0.2268          | 0.9248   |
| 0.1817        | 2.0   | 32726 | 0.2335          | 0.9347   |
| 0.0863        | 3.0   | 49089 | 0.3014          | 0.9401   |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.1+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
