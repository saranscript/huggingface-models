---
language:
- sw
tags:
- generated_from_trainer
datasets:
- tydiqa
model-index:
- name: afriberta_base-finetuned-tydiqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# afriberta_base-finetuned-tydiqa

This model is a fine-tuned version of [castorini/afriberta_base](https://huggingface.co/castorini/afriberta_base) on the tydiqa dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3728

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 192  | 2.1359          |
| No log        | 2.0   | 384  | 2.3409          |
| 0.8353        | 3.0   | 576  | 2.3728          |


### Framework versions

- Transformers 4.14.1
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
