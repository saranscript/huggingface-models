---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- matthews_correlation
model-index:
- name: distilbert-base-uncased-finetuned-cola
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-cola

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0008
- Matthews Correlation: 1.0

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

| Training Loss | Epoch | Step | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:----:|:---------------:|:--------------------:|
| No log        | 1.0   | 130  | 0.0166          | 1.0                  |
| No log        | 2.0   | 260  | 0.0054          | 1.0                  |
| No log        | 3.0   | 390  | 0.0029          | 1.0                  |
| 0.0968        | 4.0   | 520  | 0.0019          | 1.0                  |
| 0.0968        | 5.0   | 650  | 0.0014          | 1.0                  |
| 0.0968        | 6.0   | 780  | 0.0011          | 1.0                  |
| 0.0968        | 7.0   | 910  | 0.0010          | 1.0                  |
| 0.0018        | 8.0   | 1040 | 0.0008          | 1.0                  |
| 0.0018        | 9.0   | 1170 | 0.0008          | 1.0                  |
| 0.0018        | 10.0  | 1300 | 0.0008          | 1.0                  |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
