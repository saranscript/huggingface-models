---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- squad
metrics:
- rouge
model_index:
- name: t5-small-finetuned-xsum-2
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: squad
      type: squad
      args: plain_text
    metric:
      name: Rouge1
      type: rouge
      value: 28.8137
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-xsum-2

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 1.9536
- Rouge1: 28.8137
- Rouge2: 9.1265
- Rougel: 26.0238
- Rougelsum: 26.0217
- Gen Len: 13.854

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
- train_batch_size: 10
- eval_batch_size: 10
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:-----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 2.2142        | 1.0   | 8760  | 1.9994          | 29.007  | 9.2583 | 26.2377 | 26.2356   | 13.4546 |
| 2.1372        | 2.0   | 17520 | 1.9622          | 29.1077 | 9.445  | 26.3734 | 26.3687   | 13.6995 |
| 2.0755        | 3.0   | 26280 | 1.9536          | 28.8137 | 9.1265 | 26.0238 | 26.0217   | 13.854  |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
