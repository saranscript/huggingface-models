---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: distilbert-base-uncased-finetuned-yahd-twval-hptune
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-yahd-twval-hptune

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 6.3727
- Accuracy: 0.2039

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 6e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 2.1638        | 1.0   | 10106 | 2.1944          | 0.3646   |
| 1.7982        | 2.0   | 20212 | 2.6390          | 0.3333   |
| 1.3279        | 3.0   | 30318 | 3.1526          | 0.3095   |
| 0.8637        | 4.0   | 40424 | 4.8368          | 0.2470   |
| 0.5727        | 5.0   | 50530 | 6.3727          | 0.2039   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
