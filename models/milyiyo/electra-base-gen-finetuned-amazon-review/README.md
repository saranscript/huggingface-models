---
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
- name: electra-base-gen-finetuned-amazon-review
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
      value: 0.5024
    - name: F1
      type: f1
      value: 0.5063190059782597
    - name: Precision
      type: precision
      value: 0.5121183330982292
    - name: Recall
      type: recall
      value: 0.5024
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# electra-base-gen-finetuned-amazon-review

This model is a fine-tuned version of [mrm8488/electricidad-base-generator](https://huggingface.co/mrm8488/electricidad-base-generator) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 1.8030
- Accuracy: 0.5024
- F1: 0.5063
- Precision: 0.5121
- Recall: 0.5024

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
- num_epochs: 7

### Training results

| Training Loss | Epoch | Step | Accuracy | F1     | Validation Loss | Precision | Recall |
|:-------------:|:-----:|:----:|:--------:|:------:|:---------------:|:---------:|:------:|
| 0.5135        | 1.0   | 1000 | 0.4886   | 0.4929 | 1.6580          | 0.5077    | 0.4886 |
| 0.4138        | 2.0   | 2000 | 0.5044   | 0.5093 | 1.7951          | 0.5183    | 0.5044 |
| 0.4244        | 3.0   | 3000 | 0.5022   | 0.5068 | 1.8108          | 0.5141    | 0.5022 |
| 0.4231        | 6.0   | 6000 | 1.7636   | 0.4972 | 0.5018          | 0.5092    | 0.4972 |
| 0.3574        | 7.0   | 7000 | 1.8030   | 0.5024 | 0.5063          | 0.5121    | 0.5024 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
