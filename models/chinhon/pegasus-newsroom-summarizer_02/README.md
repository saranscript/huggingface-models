---
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: pegasus-newsroom-summarizer_02
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# pegasus-newsroom-summarizer_02

This model is a fine-tuned version of [google/pegasus-newsroom](https://huggingface.co/google/pegasus-newsroom) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2204
- Rouge1: 52.4459
- Rouge2: 35.2568
- Rougel: 41.6213
- Rougelsum: 48.7859
- Gen Len: 98.0627

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
| 1.3231        | 1.0   | 16113 | 1.2305          | 52.1565 | 34.8681 | 41.3189 | 48.4258   | 95.9049 |
| 1.3001        | 2.0   | 32226 | 1.2186          | 52.4921 | 35.2661 | 41.6264 | 48.8168   | 98.9241 |
| 1.2372        | 3.0   | 48339 | 1.2204          | 52.4459 | 35.2568 | 41.6213 | 48.7859   | 98.0627 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
