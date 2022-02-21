---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model_index:
  name: bert-base-uncased-sst2-membership-attack
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-sst2-membership-attack

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6296
- Accuracy: 0.8681

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.6921        | 1.0   | 3813  | 0.6263          | 0.8360   |
| 0.6916        | 2.0   | 7626  | 0.6296          | 0.8681   |
| 0.6904        | 3.0   | 11439 | 0.6105          | 0.8406   |
| 0.6886        | 4.0   | 15252 | 0.6192          | 0.8200   |
| 0.6845        | 5.0   | 19065 | 0.6250          | 0.7798   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.8.1
- Datasets 1.11.0
- Tokenizers 0.10.1
