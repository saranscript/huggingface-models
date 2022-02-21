---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: SAE-distilbert-base-uncased
  results: []
widget:
- text: "Wind noise was detected coming from the car [MASK] closure system."
  example_title: "Closure system"
 
---

# SAE-distilbert-base-uncased

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the [jgammack/SAE-door-abstracts](https://huggingface.co/datasets/jgammack/SAE-door-abstracts) dataset.

It achieves the following results on the evaluation set:
- Loss: 2.2970

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 15
- eval_batch_size: 15
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.5323        | 1.0   | 37   | 2.4503          |
| 2.4968        | 2.0   | 74   | 2.4571          |
| 2.4688        | 3.0   | 111  | 2.4099          |
| 2.419         | 4.0   | 148  | 2.3343          |
| 2.4229        | 5.0   | 185  | 2.3072          |
| 2.4067        | 6.0   | 222  | 2.2927          |
| 2.3877        | 7.0   | 259  | 2.2836          |
| 2.374         | 8.0   | 296  | 2.3767          |
| 2.3582        | 9.0   | 333  | 2.2493          |
| 2.356         | 10.0  | 370  | 2.2847          |
| 2.3294        | 11.0  | 407  | 2.3234          |
| 2.3358        | 12.0  | 444  | 2.2660          |
| 2.3414        | 13.0  | 481  | 2.2887          |
| 2.3154        | 14.0  | 518  | 2.3737          |
| 2.311         | 15.0  | 555  | 2.2686          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
