---
license: mit
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: bart-large-cnn-summarizer_03
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-large-cnn-summarizer_03

This model is a fine-tuned version of [facebook/bart-large-cnn](https://huggingface.co/facebook/bart-large-cnn) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0999
- Rouge1: 51.6222
- Rouge2: 33.428
- Rougel: 40.2093
- Rougelsum: 47.7154
- Gen Len: 102.7962

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

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2  | Rougel  | Rougelsum | Gen Len  |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:-------:|:-------:|:---------:|:--------:|
| 0.9348        | 1.0   | 17166 | 0.9969          | 51.0763 | 32.9497 | 39.6851 | 47.0744   | 99.664   |
| 0.7335        | 2.0   | 34332 | 1.0019          | 51.8002 | 33.8081 | 40.5887 | 47.9445   | 99.7884  |
| 0.471         | 3.0   | 51498 | 1.0999          | 51.6222 | 33.428  | 40.2093 | 47.7154   | 102.7962 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
