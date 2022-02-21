---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-newsroom-headline_writer
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-newsroom-headline_writer

This model is a fine-tuned version of [google/pegasus-newsroom](https://huggingface.co/google/pegasus-newsroom) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3988
- Rouge1: 41.8748
- Rouge2: 23.1947
- Rougel: 35.6263
- Rougelsum: 35.7355
- Gen Len: 34.1266

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
- train_batch_size: 1
- eval_batch_size: 1
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:-------:|
| 1.5784        | 1.0   | 31200 | 1.4287          | 41.4257 | 22.9355 | 35.3299 | 35.4648   | 34.4677 |
| 1.3501        | 2.0   | 62400 | 1.3955          | 41.9119 | 23.1912 | 35.6698 | 35.7479   | 33.8672 |
| 1.2417        | 3.0   | 93600 | 1.3988          | 41.8748 | 23.1947 | 35.6263 | 35.7355   | 34.1266 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
