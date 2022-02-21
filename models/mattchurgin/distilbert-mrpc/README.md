---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
- f1
model-index:
- name: distilbert-mrpc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: mrpc
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8480392156862745
    - name: F1
      type: f1
      value: 0.8934707903780068
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-mrpc

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6783
- Accuracy: 0.8480
- F1: 0.8935

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| 0.5916        | 0.22  | 100  | 0.5676          | 0.7157   | 0.8034 |
| 0.5229        | 0.44  | 200  | 0.4534          | 0.7770   | 0.8212 |
| 0.5055        | 0.65  | 300  | 0.4037          | 0.8137   | 0.8762 |
| 0.4597        | 0.87  | 400  | 0.3706          | 0.8407   | 0.8893 |
| 0.4           | 1.09  | 500  | 0.4590          | 0.8113   | 0.8566 |
| 0.3498        | 1.31  | 600  | 0.4196          | 0.8554   | 0.8974 |
| 0.2916        | 1.53  | 700  | 0.4606          | 0.8554   | 0.8933 |
| 0.3309        | 1.74  | 800  | 0.5162          | 0.8578   | 0.9027 |
| 0.3788        | 1.96  | 900  | 0.3911          | 0.8529   | 0.8980 |
| 0.2059        | 2.18  | 1000 | 0.5842          | 0.8554   | 0.8995 |
| 0.1595        | 2.4   | 1100 | 0.5701          | 0.8578   | 0.8975 |
| 0.1205        | 2.61  | 1200 | 0.6905          | 0.8407   | 0.8889 |
| 0.174         | 2.83  | 1300 | 0.6783          | 0.8480   | 0.8935 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.1
- Datasets 1.17.0
- Tokenizers 0.10.3
