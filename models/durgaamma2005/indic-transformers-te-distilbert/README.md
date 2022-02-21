---
tags:
- generated_from_trainer
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: indic-transformers-te-distilbert
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann
      type: wikiann
      args: te
    metrics:
    - name: Precision
      type: precision
      value: 0.5657225853304285
    - name: Recall
      type: recall
      value: 0.6486261448792673
    - name: F1
      type: f1
      value: 0.604344453064391
    - name: Accuracy
      type: accuracy
      value: 0.9049186160277506
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# indic-transformers-te-distilbert

This model was trained from scratch on the wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2940
- Precision: 0.5657
- Recall: 0.6486
- F1: 0.6043
- Accuracy: 0.9049

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 125  | 0.3629          | 0.4855    | 0.5287 | 0.5062 | 0.8826   |
| No log        | 2.0   | 250  | 0.3032          | 0.5446    | 0.6303 | 0.5843 | 0.9002   |
| No log        | 3.0   | 375  | 0.2940          | 0.5657    | 0.6486 | 0.6043 | 0.9049   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
