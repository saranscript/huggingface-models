---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
- f1
model_index:
- name: finetuned-bert
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: mrpc
    metric:
      name: F1
      type: f1
      value: 0.9125214408233276
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# finetuned-bert

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3916
- Accuracy: 0.875
- F1: 0.9125

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
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| 0.581         | 1.0   | 230  | 0.4086          | 0.8260   | 0.8711 |
| 0.366         | 2.0   | 460  | 0.3758          | 0.8480   | 0.8963 |
| 0.2328        | 3.0   | 690  | 0.3916          | 0.875    | 0.9125 |


### Framework versions

- Transformers 4.9.0.dev0
- Pytorch 1.8.1+cu111
- Datasets 1.8.1.dev0
- Tokenizers 0.10.1
