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
model-index:
- name: test-bert-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metrics:
    - name: Precision
      type: precision
      value: 0.9354625186165811
    - name: Recall
      type: recall
      value: 0.9513631773813531
    - name: F1
      type: f1
      value: 0.943345848977889
    - name: Accuracy
      type: accuracy
      value: 0.9867545770294931
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# test-bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0600
- Precision: 0.9355
- Recall: 0.9514
- F1: 0.9433
- Accuracy: 0.9868

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
| 0.0849        | 1.0   | 1756 | 0.0713          | 0.9144    | 0.9366 | 0.9253 | 0.9817   |
| 0.0359        | 2.0   | 3512 | 0.0658          | 0.9346    | 0.9500 | 0.9422 | 0.9860   |
| 0.0206        | 3.0   | 5268 | 0.0600          | 0.9355    | 0.9514 | 0.9433 | 0.9868   |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.8.1+cu111
- Datasets 1.12.1.dev0
- Tokenizers 0.10.3
