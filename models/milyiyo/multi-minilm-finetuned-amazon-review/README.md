---
license: mit
tags:
- generated_from_trainer
datasets:
- amazon_reviews_multi
metrics:
- accuracy
- f1
- precision
- recall
model-index:
- name: multi-minilm-finetuned-amazon-review
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: amazon_reviews_multi
      type: amazon_reviews_multi
      args: es
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.5422
    - name: F1
      type: f1
      value: 0.543454465221178
    - name: Precision
      type: precision
      value: 0.5452336215624385
    - name: Recall
      type: recall
      value: 0.5422
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# multi-minilm-finetuned-amazon-review

This model is a fine-tuned version of [microsoft/Multilingual-MiniLM-L12-H384](https://huggingface.co/microsoft/Multilingual-MiniLM-L12-H384) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2436
- Accuracy: 0.5422
- F1: 0.5435
- Precision: 0.5452
- Recall: 0.5422

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|:------:|:---------:|:------:|
| 1.0049        | 1.0   | 2500  | 1.0616          | 0.5352   | 0.5268 | 0.5347    | 0.5352 |
| 0.9172        | 2.0   | 5000  | 1.0763          | 0.5432   | 0.5412 | 0.5444    | 0.5432 |
| 0.8285        | 3.0   | 7500  | 1.1077          | 0.5408   | 0.5428 | 0.5494    | 0.5408 |
| 0.7361        | 4.0   | 10000 | 1.1743          | 0.5342   | 0.5399 | 0.5531    | 0.5342 |
| 0.6538        | 5.0   | 12500 | 1.2436          | 0.5422   | 0.5435 | 0.5452    | 0.5422 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
