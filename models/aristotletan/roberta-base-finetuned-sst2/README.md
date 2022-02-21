---
license: mit
tags:
- generated_from_trainer
datasets:
- scim
metrics:
- accuracy
model_index:
- name: roberta-base-finetuned-sst2
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: scim
      type: scim
      args: eod
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9111111111111111
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-finetuned-sst2

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the scim dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4632
- Accuracy: 0.9111

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
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 90   | 2.0273          | 0.6667   |
| No log        | 2.0   | 180  | 0.8802          | 0.8556   |
| No log        | 3.0   | 270  | 0.5908          | 0.8889   |
| No log        | 4.0   | 360  | 0.4632          | 0.9111   |
| No log        | 5.0   | 450  | 0.4294          | 0.9111   |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
