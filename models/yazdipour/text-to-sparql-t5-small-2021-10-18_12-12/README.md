---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model-index:
- name: text-to-sparql-t5-small-2021-10-18_12-12
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-small-2021-10-18_12-12

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3284
- Gen Len: 19.0
- Bertscorer-p: 0.5420
- Bertscorer-r: 0.0732
- Bertscorer-f1: 0.2972
- Sacrebleu-score: 4.8763
- Sacrebleu-precisions: [87.2581084764241, 73.48869132519009, 64.19139944127409, 58.342420937840785]
- Bleu-bp: 0.0697

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Gen Len | Bertscorer-p | Bertscorer-r | Bertscorer-f1 | Sacrebleu-score | Sacrebleu-precisions                                                         | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------------:|:------------:|:-------------:|:---------------:|:----------------------------------------------------------------------------:|:-------:|
| 0.4209        | 1.0   | 4772 | 0.3284          | 19.0    | 0.5420       | 0.0732       | 0.2972        | 4.8763          | [87.2581084764241, 73.48869132519009, 64.19139944127409, 58.342420937840785] | 0.0697  |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
