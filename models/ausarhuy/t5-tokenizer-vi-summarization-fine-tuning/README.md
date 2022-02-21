---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- rouge
model-index:
- name: t5-tokenizer-vi-summarization-fine-tuning
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-tokenizer-vi-summarization-fine-tuning

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.5004
- Rouge1: 2.5115
- Rouge2: 1.6283
- Rougel: 2.1956
- Rougelsum: 2.3133

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
- num_epochs: 20
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|
| No log        | 1.0   | 18   | 2.9736          | 7.4562  | 4.7953 | 6.5821  | 7.0011    |
| No log        | 2.0   | 36   | 2.8374          | 10.4004 | 6.5797 | 8.9923  | 9.5457    |
| No log        | 3.0   | 54   | 2.7639          | 11.4207 | 6.9529 | 9.8551  | 10.5204   |
| No log        | 4.0   | 72   | 2.7031          | 13.0109 | 8.0495 | 11.2006 | 11.9397   |
| No log        | 5.0   | 90   | 2.6545          | 13.9192 | 8.5749 | 11.9778 | 12.6609   |
| No log        | 6.0   | 108  | 2.6232          | 12.4863 | 7.4892 | 10.8398 | 11.5602   |
| No log        | 7.0   | 126  | 2.5953          | 11.0754 | 6.922  | 9.5014  | 10.2023   |
| No log        | 8.0   | 144  | 2.5774          | 9.5541  | 6.3021 | 8.2687  | 8.7284    |
| No log        | 9.0   | 162  | 2.5592          | 8.1885  | 5.3888 | 7.0848  | 7.5366    |
| No log        | 10.0  | 180  | 2.5476          | 6.9352  | 4.7275 | 5.9785  | 6.3626    |
| No log        | 11.0  | 198  | 2.5398          | 6.0634  | 4.2445 | 5.4142  | 5.7681    |
| No log        | 12.0  | 216  | 2.5329          | 3.8984  | 2.7881 | 3.4573  | 3.6614    |
| No log        | 13.0  | 234  | 2.5251          | 3.8638  | 2.7625 | 3.5149  | 3.6564    |
| No log        | 14.0  | 252  | 2.5158          | 3.393   | 2.5359 | 3.1226  | 3.2294    |
| No log        | 15.0  | 270  | 2.5113          | 2.8226  | 1.8936 | 2.4672  | 2.6043    |
| No log        | 16.0  | 288  | 2.5096          | 2.5115  | 1.6283 | 2.1956  | 2.3133    |
| No log        | 17.0  | 306  | 2.5048          | 2.5115  | 1.6283 | 2.1956  | 2.3133    |
| No log        | 18.0  | 324  | 2.5025          | 2.5115  | 1.6283 | 2.1956  | 2.3133    |
| No log        | 19.0  | 342  | 2.5006          | 2.5115  | 1.6283 | 2.1956  | 2.3133    |
| No log        | 20.0  | 360  | 2.5004          | 2.5115  | 1.6283 | 2.1956  | 2.3133    |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
