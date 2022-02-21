---
license: mit
tags:
- generated_from_trainer
model-index:
- name: bert-base-italian-xxl-uncased-finetuned-ComunaliRoma
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-italian-xxl-uncased-finetuned-ComunaliRoma

This model is a fine-tuned version of [dbmdz/bert-base-italian-xxl-uncased](https://huggingface.co/dbmdz/bert-base-italian-xxl-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.5095

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 2.6717        | 1.0   | 1014 | 2.6913          |
| 2.4869        | 2.0   | 2028 | 2.5843          |
| 2.3411        | 3.0   | 3042 | 2.5095          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
