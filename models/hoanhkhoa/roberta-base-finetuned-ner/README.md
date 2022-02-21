---
license: mit
tags:
- generated_from_trainer
datasets:
- null
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: roberta-base-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9914674251177673
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-finetuned-ner

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0381
- Precision: 0.9469
- Recall: 0.9530
- F1: 0.9500
- Accuracy: 0.9915

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
| 0.1328        | 1.0   | 753  | 0.0492          | 0.9143    | 0.9308 | 0.9225 | 0.9884   |
| 0.0301        | 2.0   | 1506 | 0.0378          | 0.9421    | 0.9474 | 0.9448 | 0.9910   |
| 0.0185        | 3.0   | 2259 | 0.0381          | 0.9469    | 0.9530 | 0.9500 | 0.9915   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
