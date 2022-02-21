---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: albert-base-v2-finetuned-rte
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: rte
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.7581227436823105
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-base-v2-finetuned-rte

This model is a fine-tuned version of [albert-base-v2](https://huggingface.co/albert-base-v2) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2496
- Accuracy: 0.7581

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
- train_batch_size: 10
- eval_batch_size: 10
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 249  | 0.5914          | 0.6751   |
| No log        | 2.0   | 498  | 0.5843          | 0.7184   |
| 0.5873        | 3.0   | 747  | 0.6925          | 0.7220   |
| 0.5873        | 4.0   | 996  | 1.1613          | 0.7545   |
| 0.2149        | 5.0   | 1245 | 1.2496          | 0.7581   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
