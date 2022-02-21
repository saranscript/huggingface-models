---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: SAE-bert-base-uncased
  results: []
widget:
- text: "Wind [MASK] was detected coming from the car door closure system."
  example_title: "Closure system"
 
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# SAE-bert-base-uncased

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the [jgammack/SAE-door-abstracts](https://huggingface.co/datasets/jgammack/SAE-door-abstracts) dataset.

It achieves the following results on the evaluation set:
- Loss: 2.1256

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
- train_batch_size: 7
- eval_batch_size: 7
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.5967        | 1.0   | 80   | 2.3409          |
| 2.4881        | 2.0   | 160  | 2.2707          |
| 2.3567        | 3.0   | 240  | 2.3134          |
| 2.3413        | 4.0   | 320  | 2.2592          |
| 2.3006        | 5.0   | 400  | 2.2351          |
| 2.2568        | 6.0   | 480  | 2.2556          |
| 2.2303        | 7.0   | 560  | 2.2546          |
| 2.1892        | 8.0   | 640  | 2.1868          |
| 2.1851        | 9.0   | 720  | 2.2073          |
| 2.1738        | 10.0  | 800  | 2.1344          |
| 2.1673        | 11.0  | 880  | 2.1927          |
| 2.1518        | 12.0  | 960  | 2.1844          |
| 2.1142        | 13.0  | 1040 | 2.1466          |
| 2.1343        | 14.0  | 1120 | 2.2024          |
| 2.1332        | 15.0  | 1200 | 2.1035          |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
