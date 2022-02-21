---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- matthews_correlation
model-index:
- name: distilbert-base-uncased-finetuned-cola-3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-cola-3

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0002
- Matthews Correlation: 1.0


Label 0 : "AIMX"
Label 1 : "OWNX"
Label 2 : "CONT"
Label 3 : "BASE"
Label 4 : "MISC"



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
| No log        | 1.0   | 192  | 0.0060          | 1.0                  |
| No log        | 2.0   | 384  | 0.0019          | 1.0                  |
| 0.0826        | 3.0   | 576  | 0.0010          | 1.0                  |
| 0.0826        | 4.0   | 768  | 0.0006          | 1.0                  |
| 0.0826        | 5.0   | 960  | 0.0005          | 1.0                  |
| 0.001         | 6.0   | 1152 | 0.0004          | 1.0                  |
| 0.001         | 7.0   | 1344 | 0.0003          | 1.0                  |
| 0.0005        | 8.0   | 1536 | 0.0003          | 1.0                  |
| 0.0005        | 9.0   | 1728 | 0.0002          | 1.0                  |
| 0.0005        | 10.0  | 1920 | 0.0002          | 1.0                  |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
