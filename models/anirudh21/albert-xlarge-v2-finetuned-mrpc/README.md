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
- name: albert-xlarge-v2-finetuned-mrpc
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
      value: 0.7132352941176471
    - name: F1
      type: f1
      value: 0.8145800316957211
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-xlarge-v2-finetuned-mrpc

This model is a fine-tuned version of [albert-xlarge-v2](https://huggingface.co/albert-xlarge-v2) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5563
- Accuracy: 0.7132
- F1: 0.8146

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

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 63   | 0.6898          | 0.5221   | 0.6123 |
| No log        | 2.0   | 126  | 0.6298          | 0.6838   | 0.8122 |
| No log        | 3.0   | 189  | 0.6043          | 0.7010   | 0.8185 |
| No log        | 4.0   | 252  | 0.5834          | 0.7010   | 0.8146 |
| No log        | 5.0   | 315  | 0.5563          | 0.7132   | 0.8146 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
