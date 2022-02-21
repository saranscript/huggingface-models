---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- mlsum
metrics:
- rouge
model-index:
- name: mt5-small-finetuned-mlsum
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: mlsum
      type: mlsum
      args: es
    metrics:
    - name: Rouge1
      type: rouge
      value: 1.1475
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# mt5-small-finetuned-mlsum

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on the mlsum dataset.
It achieves the following results on the evaluation set:
- Loss: nan
- Rouge1: 1.1475
- Rouge2: 0.1284
- Rougel: 1.0634
- Rougelsum: 1.0778
- Gen Len: 3.7939

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
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1 | Rouge2 | Rougel | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:------:|:------:|:------:|:---------:|:-------:|
| nan           | 1.0   | 808  | nan             | 1.1475 | 0.1284 | 1.0634 | 1.0778    | 3.7939  |


### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
