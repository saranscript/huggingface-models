---
license: mit
tags:
- generated_from_trainer
model-index:
- name: xlm-roberta-base-finetuned-marc-en
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-base-finetuned-marc-en

This model is a fine-tuned version of [xlm-roberta-base](https://huggingface.co/xlm-roberta-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1440
- Acc: 0.9706

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Acc    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 0.5419        | 1.0   | 1475 | 0.4134          | 0.9137 |
| 0.2723        | 2.0   | 2950 | 0.2306          | 0.9441 |
| 0.1822        | 3.0   | 4425 | 0.1701          | 0.9614 |
| 0.1398        | 4.0   | 5900 | 0.1480          | 0.9686 |
| 0.1043        | 5.0   | 7375 | 0.1440          | 0.9706 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
