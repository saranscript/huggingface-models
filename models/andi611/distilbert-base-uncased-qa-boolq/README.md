---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- boolq
metrics:
- accuracy
model_index:
- name: distilbert-base-uncased-boolq
  results:
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: boolq
      type: boolq
      args: default
    metric:
      name: Accuracy
      type: accuracy
      value: 0.7314984709480122
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-boolq

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the boolq dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2071
- Accuracy: 0.7315

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
- train_batch_size: 16
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.6506        | 1.0   | 531  | 0.6075          | 0.6681   |
| 0.575         | 2.0   | 1062 | 0.5816          | 0.6978   |
| 0.4397        | 3.0   | 1593 | 0.6137          | 0.7253   |
| 0.2524        | 4.0   | 2124 | 0.8124          | 0.7466   |
| 0.126         | 5.0   | 2655 | 1.1437          | 0.7370   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
