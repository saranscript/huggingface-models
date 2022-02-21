---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: finetuned-T5-UK-financial-summarization
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# finetuned-T5-UK-financial-summarization

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3276
- Rouge1: 49.5834
- Rouge2: 34.5668
- Rougel: 37.6179
- Rougelsum: 46.0004
- Gen Len: 490.0579

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 2
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 4.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1 | Rouge2 | Rougel | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|:------:|:---------:|:-------:|
| 0.8064        | 0.67  | 1000 | 0.4376          | 5.8905 | 3.8332 | 5.1982 | 5.5451    | 19.0    |
| 0.486         | 1.34  | 2000 | 0.3717          | 6.3056 | 4.3892 | 5.6589 | 6.0154    | 19.0    |
| 0.4492        | 2.01  | 3000 | 0.3427          | 6.4831 | 4.595  | 5.809  | 6.1753    | 19.0    |
| 0.4138        | 2.68  | 4000 | 0.3362          | 6.4667 | 4.5705 | 5.8081 | 6.1579    | 19.0    |
| 0.3697        | 3.34  | 5000 | 0.3284          | 6.5319 | 4.6032 | 5.8458 | 6.2253    | 19.0    |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.7.0
- Datasets 1.17.0
- Tokenizers 0.11.0
