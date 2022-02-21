---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: portuguese-archival-finding-aids
  results:
  - task:
      name: Token Classification
      type: token-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9617770479839446
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# portuguese-archival-finding-aids

This model is a fine-tuned version of [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1812
- Precision: 0.8624
- Recall: 0.9557
- F1: 0.9067
- Accuracy: 0.9618

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 192  | 0.1565          | 0.8511    | 0.9327 | 0.8900 | 0.9563   |
| 0.1849        | 2.0   | 384  | 0.1594          | 0.8634    | 0.9543 | 0.9065 | 0.9619   |
| 0.0454        | 3.0   | 576  | 0.1812          | 0.8624    | 0.9557 | 0.9067 | 0.9618   |


### Framework versions

- Transformers 4.10.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.10.2
- Tokenizers 0.10.3
