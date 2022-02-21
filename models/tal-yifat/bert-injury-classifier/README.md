---
tags:
- generated_from_trainer
metrics:
- accuracy
model-index:
- name: bert-injury-classifier
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-injury-classifier

This model was trained from scratch on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6915
- Accuracy: 0.5298

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.6676        | 1.0   | 19026 | 0.6635          | 0.6216   |
| 0.6915        | 2.0   | 38052 | 0.6915          | 0.5298   |
| 0.6924        | 3.0   | 57078 | 0.6915          | 0.5298   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
