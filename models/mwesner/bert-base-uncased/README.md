---
tags:
- generated_from_trainer
model-index:
- name: bert-base-uncased
  results: []
---


# bert-base-uncased

This model was trained on a dataset of issues from github.
It achieves the following results on the evaluation set:
- Loss: 1.2437

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

Masked language model trained on github issue data with token length of 128.

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 1
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 16

### Training results

| Training Loss | Epoch | Step   | Validation Loss |
|:-------------:|:-----:|:------:|:---------------:|
| 2.205         | 1.0   | 9303   | 1.7893          |
| 1.8417        | 2.0   | 18606  | 1.7270          |
| 1.7103        | 3.0   | 27909  | 1.6650          |
| 1.6014        | 4.0   | 37212  | 1.6052          |
| 1.523         | 5.0   | 46515  | 1.5782          |
| 1.4588        | 6.0   | 55818  | 1.4836          |
| 1.3922        | 7.0   | 65121  | 1.4289          |
| 1.317         | 8.0   | 74424  | 1.4414          |
| 1.2622        | 9.0   | 83727  | 1.4322          |
| 1.2123        | 10.0  | 93030  | 1.3651          |
| 1.1753        | 11.0  | 102333 | 1.3636          |
| 1.1164        | 12.0  | 111636 | 1.2872          |
| 1.0636        | 13.0  | 120939 | 1.3705          |
| 1.021         | 14.0  | 130242 | 1.3013          |
| 0.996         | 15.0  | 139545 | 1.2756          |
| 0.9625        | 16.0  | 148848 | 1.2437          |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.9.0
- Datasets 1.11.0
- Tokenizers 0.10.3
