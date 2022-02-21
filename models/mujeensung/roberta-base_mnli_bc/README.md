---
language:
- en
license: mit
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: roberta-base_mnli_bc
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
      value: 0.9583768461882739
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base_mnli_bc

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the GLUE MNLI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2125
- Accuracy: 0.9584

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
| 0.2015        | 1.0   | 16363 | 0.1820          | 0.9470   |
| 0.1463        | 2.0   | 32726 | 0.1909          | 0.9559   |
| 0.0768        | 3.0   | 49089 | 0.2117          | 0.9585   |


### Framework versions

- Transformers 4.13.0
- Pytorch 1.10.1+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
