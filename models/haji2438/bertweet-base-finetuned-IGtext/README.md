---
tags:
- generated_from_trainer
model-index:
- name: bertweet-base-finetuned-IGtext
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bertweet-base-finetuned-IGtext

This model is a fine-tuned version of [vinai/bertweet-base](https://huggingface.co/vinai/bertweet-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0334

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
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.6741        | 1.0   | 505  | 2.2096          |
| 2.3183        | 2.0   | 1010 | 2.0934          |
| 2.2089        | 3.0   | 1515 | 2.0595          |
| 2.1473        | 4.0   | 2020 | 2.0246          |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
