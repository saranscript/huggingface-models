---
license: apache-2.0
tags:
- summarization
metrics:
- rouge
model-index:
- name: POCTS
  results:
  - task:
      name: Summarization
      type: summarization
    metrics:
    - name: Rouge1
      type: rouge
      value: 26.1391
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# POCTS

This model is a fine-tuned version of [facebook/bart-large](https://huggingface.co/facebook/bart-large) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0970
- Rouge1: 26.1391
- Rouge2: 7.3101
- Rougel: 19.1217
- Rougelsum: 21.9706
- Gen Len: 46.2245

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_ratio: 0.15
- num_epochs: 3.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:------:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| 3.3259        | 1.0   | 33875  | 3.2535          | 17.942  | 4.5143 | 14.2766 | 15.582    | 19.3901 |
| 2.9764        | 2.0   | 67750  | 3.1278          | 18.6558 | 5.1844 | 15.0939 | 16.3367   | 19.9174 |
| 2.5889        | 3.0   | 101625 | 3.0970          | 19.1763 | 5.4517 | 15.5342 | 16.7186   | 19.8855 |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1+cu110
- Datasets 1.11.0
- Tokenizers 0.10.3
