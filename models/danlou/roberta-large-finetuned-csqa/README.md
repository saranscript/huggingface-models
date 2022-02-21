---
license: mit
tags:
- generated_from_trainer
datasets:
- commonsense_qa
metrics:
- accuracy
model_index:
- name: roberta-large-finetuned-csqa
  results:
  - dataset:
      name: commonsense_qa
      type: commonsense_qa
      args: default
    metric:
      name: Accuracy
      type: accuracy
      value: 0.7330057621002197
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-large-finetuned-csqa

This model is a fine-tuned version of [roberta-large](https://huggingface.co/roberta-large) on the commonsense_qa dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9146
- Accuracy: 0.7330

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 1.3903        | 1.0   | 609  | 0.8845          | 0.6642   |
| 0.8939        | 2.0   | 1218 | 0.7054          | 0.7281   |
| 0.6163        | 3.0   | 1827 | 0.7452          | 0.7314   |
| 0.4245        | 4.0   | 2436 | 0.8369          | 0.7355   |
| 0.3258        | 5.0   | 3045 | 0.9146          | 0.7330   |


### Framework versions

- Transformers 4.9.0
- Pytorch 1.9.0
- Datasets 1.10.2
- Tokenizers 0.10.3
