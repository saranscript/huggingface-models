---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- emotion
metrics:
- f1
model-index:
- name: bert-base-cased-finetuned-emotion
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: emotion
      type: emotion
      args: default
    metrics:
    - name: F1
      type: f1
      value: 0.9365323747830425
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-cased-finetuned-emotion

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the emotion dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1342
- F1: 0.9365

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
- train_batch_size: 64
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | F1     |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.7357        | 1.0   | 250  | 0.2318          | 0.9224 |
| 0.1758        | 2.0   | 500  | 0.1679          | 0.9349 |
| 0.1228        | 3.0   | 750  | 0.1385          | 0.9382 |
| 0.0961        | 4.0   | 1000 | 0.1452          | 0.9340 |
| 0.0805        | 5.0   | 1250 | 0.1342          | 0.9365 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
