---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: distilbert-base-uncased-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metric:
      name: Accuracy
      type: accuracy
      value: 0.985193893275295
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-ner

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0664
- Precision: 0.9332
- Recall: 0.9423
- F1: 0.9377
- Accuracy: 0.9852

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 16
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2042        | 1.0   | 878  | 0.0636          | 0.9230    | 0.9253 | 0.9241 | 0.9822   |
| 0.0428        | 2.0   | 1756 | 0.0577          | 0.9286    | 0.9370 | 0.9328 | 0.9841   |
| 0.0199        | 3.0   | 2634 | 0.0606          | 0.9364    | 0.9401 | 0.9383 | 0.9851   |
| 0.0121        | 4.0   | 3512 | 0.0641          | 0.9339    | 0.9380 | 0.9360 | 0.9847   |
| 0.0079        | 5.0   | 4390 | 0.0664          | 0.9332    | 0.9423 | 0.9377 | 0.9852   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
