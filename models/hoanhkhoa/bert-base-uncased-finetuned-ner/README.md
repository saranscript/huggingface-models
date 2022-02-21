---
license: apache-2.0
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
- name: bert-base-uncased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9853695435592783
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-ner

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0604
- Precision: 0.9247
- Recall: 0.9343
- F1: 0.9295
- Accuracy: 0.9854

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
| 0.2082        | 1.0   | 753  | 0.0657          | 0.8996    | 0.9256 | 0.9125 | 0.9821   |
| 0.0428        | 2.0   | 1506 | 0.0595          | 0.9268    | 0.9343 | 0.9305 | 0.9848   |
| 0.0268        | 3.0   | 2259 | 0.0604          | 0.9247    | 0.9343 | 0.9295 | 0.9854   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
