---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wsj_markets
metrics:
- rouge
model_index:
- name: t5-small-finetuned-xsum
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: wsj_markets
      type: wsj_markets
      args: default
    metric:
      name: Rouge1
      type: rouge
      value: 10.4492
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-xsum

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the wsj_markets dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1447
- Rouge1: 10.4492
- Rouge2: 3.9563
- Rougel: 9.3368
- Rougelsum: 9.9828
- Gen Len: 19.0

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:------:|:---------:|:-------:|
| 2.2742        | 1.0   | 868  | 1.3135          | 9.4644  | 2.618  | 8.4048 | 8.9764    | 19.0    |
| 1.4607        | 2.0   | 1736 | 1.2134          | 9.6327  | 3.8535 | 9.0703 | 9.2466    | 19.0    |
| 1.3579        | 3.0   | 2604 | 1.1684          | 10.1616 | 3.5498 | 9.2294 | 9.4507    | 19.0    |
| 1.3314        | 4.0   | 3472 | 1.1514          | 10.0621 | 3.6907 | 9.1635 | 9.4955    | 19.0    |
| 1.3084        | 5.0   | 4340 | 1.1447          | 10.4492 | 3.9563 | 9.3368 | 9.9828    | 19.0    |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0+cu102
- Datasets 1.10.0
- Tokenizers 0.10.3
