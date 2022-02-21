---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- ingredients_yes_no
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-ingredients
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: ingredients_yes_no
      type: ingredients_yes_no
      args: IngredientsYesNo
    metrics:
    - name: Precision
      type: precision
      value: 0.9898648648648649
    - name: Recall
      type: recall
      value: 0.9932203389830508
    - name: F1
      type: f1
      value: 0.9915397631133671
    - name: Accuracy
      type: accuracy
      value: 0.9978308026030369
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-ingredients

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the ingredients_yes_no dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0105
- Precision: 0.9899
- Recall: 0.9932
- F1: 0.9915
- Accuracy: 0.9978

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
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 47   | 0.2783          | 0.4       | 0.5492 | 0.4629 | 0.8910   |
| No log        | 2.0   | 94   | 0.1089          | 0.8145    | 0.8780 | 0.8450 | 0.9718   |
| No log        | 3.0   | 141  | 0.0273          | 0.9865    | 0.9932 | 0.9899 | 0.9973   |
| No log        | 4.0   | 188  | 0.0168          | 0.9865    | 0.9932 | 0.9899 | 0.9973   |
| No log        | 5.0   | 235  | 0.0156          | 0.9865    | 0.9898 | 0.9882 | 0.9957   |
| No log        | 6.0   | 282  | 0.0129          | 0.9865    | 0.9932 | 0.9899 | 0.9973   |
| No log        | 7.0   | 329  | 0.0121          | 0.9899    | 0.9932 | 0.9915 | 0.9978   |
| No log        | 8.0   | 376  | 0.0115          | 0.9899    | 0.9932 | 0.9915 | 0.9978   |
| No log        | 9.0   | 423  | 0.0108          | 0.9899    | 0.9932 | 0.9915 | 0.9978   |
| No log        | 10.0  | 470  | 0.0105          | 0.9899    | 0.9932 | 0.9915 | 0.9978   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
