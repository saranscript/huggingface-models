---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- precision
- recall
model-index:
- name: distilbert-magazine-classifier
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-magazine-classifier

This model is a fine-tuned version of [distilbert-base-cased](https://huggingface.co/distilbert-base-cased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.8377
- Precision: 0.25
- Recall: 0.125
- Fscore: 0.1667

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

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | Fscore |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|
| 0.1779        | 1.0   | 2    | 1.7584          | 0.2222    | 0.3333 | 0.2667 |
| 0.1635        | 2.0   | 4    | 1.7585          | 0.25      | 0.125  | 0.1667 |
| 0.1405        | 3.0   | 6    | 1.8377          | 0.25      | 0.125  | 0.1667 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
