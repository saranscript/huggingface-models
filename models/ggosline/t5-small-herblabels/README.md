---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: t5-small-herblabels
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-herblabels

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4823
- Rouge1: 3.0759
- Rouge2: 1.0495
- Rougel: 3.0758
- Rougelsum: 3.0431
- Gen Len: 18.9716

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1 | Rouge2 | Rougel | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|:------:|:---------:|:-------:|
| No log        | 1.0   | 264  | 1.6010          | 2.4276 | 0.5658 | 2.3546 | 2.3099    | 18.9091 |
| 2.5052        | 2.0   | 528  | 1.0237          | 2.9016 | 0.3395 | 2.8221 | 2.783     | 18.9673 |
| 2.5052        | 3.0   | 792  | 0.7793          | 2.962  | 0.3091 | 2.9375 | 2.8786    | 18.9588 |
| 1.1552        | 4.0   | 1056 | 0.6530          | 2.98   | 0.4375 | 2.9584 | 2.8711    | 18.9588 |
| 1.1552        | 5.0   | 1320 | 0.5863          | 3.0023 | 0.5882 | 2.987  | 2.9155    | 18.9588 |
| 0.8659        | 6.0   | 1584 | 0.5428          | 3.0576 | 0.8019 | 3.0494 | 2.9989    | 18.9716 |
| 0.8659        | 7.0   | 1848 | 0.5145          | 3.0808 | 0.9476 | 3.0719 | 3.0237    | 18.9716 |
| 0.747         | 8.0   | 2112 | 0.4962          | 3.0748 | 1.0032 | 3.0683 | 3.0359    | 18.9716 |
| 0.747         | 9.0   | 2376 | 0.4856          | 3.0702 | 1.0196 | 3.0665 | 3.0328    | 18.9716 |
| 0.6987        | 10.0  | 2640 | 0.4823          | 3.0759 | 1.0495 | 3.0758 | 3.0431    | 18.9716 |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0
- Datasets 1.16.1
- Tokenizers 0.10.3
