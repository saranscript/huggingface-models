---
license: apache-2.0
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
- name: distilbert-base-uncased-finetuned-amazon-review
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
      value: 0.693
    - name: F1
      type: f1
      value: 0.7002653469272611
    - name: Precision
      type: precision
      value: 0.709541681233075
    - name: Recall
      type: recall
      value: 0.693
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-amazon-review

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3494
- Accuracy: 0.693
- F1: 0.7003
- Precision: 0.7095
- Recall: 0.693

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:---------:|:------:|
| No log        | 0.5   | 500  | 0.8287          | 0.7104   | 0.7120 | 0.7152    | 0.7104 |
| 0.4238        | 1.0   | 1000 | 0.8917          | 0.7094   | 0.6989 | 0.6917    | 0.7094 |
| 0.4238        | 1.5   | 1500 | 0.9367          | 0.6884   | 0.6983 | 0.7151    | 0.6884 |
| 0.3152        | 2.0   | 2000 | 0.9845          | 0.7116   | 0.7144 | 0.7176    | 0.7116 |
| 0.3152        | 2.5   | 2500 | 1.0752          | 0.6814   | 0.6968 | 0.7232    | 0.6814 |
| 0.2454        | 3.0   | 3000 | 1.1215          | 0.6918   | 0.6954 | 0.7068    | 0.6918 |
| 0.2454        | 3.5   | 3500 | 1.2905          | 0.6976   | 0.7048 | 0.7138    | 0.6976 |
| 0.1989        | 4.0   | 4000 | 1.2938          | 0.694    | 0.7016 | 0.7113    | 0.694  |
| 0.1989        | 4.5   | 4500 | 1.3623          | 0.6972   | 0.7014 | 0.7062    | 0.6972 |
| 0.1746        | 5.0   | 5000 | 1.3494          | 0.693    | 0.7003 | 0.7095    | 0.693  |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
