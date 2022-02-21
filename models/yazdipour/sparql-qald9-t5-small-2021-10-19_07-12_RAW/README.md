---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: sparql-qald9-t5-small-2021-10-19_07-12_RAW
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sparql-qald9-t5-small-2021-10-19_07-12_RAW

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Gen Len | P      | R      | F1     | Bleu-score | Bleu-precisions                                                              | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:------:|:------:|:----------:|:----------------------------------------------------------------------------:|:-------:|
| No log        | 1.0   | 51   | 2.8581          | 19.0    | 0.3301 | 0.0433 | 0.1830 | 7.5917     | [69.82603479304139, 45.68226763348714, 32.33357717629846, 24.56861133935908] | 0.1903  |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
