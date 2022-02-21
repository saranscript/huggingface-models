---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model-index:
- name: text-to-sparql-t5-base-2021-10-18_16-15
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-base-2021-10-18_16-15

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1294
- Gen Len: 19.0
- Bertscorer-p: 0.5827
- Bertscorer-r: 0.0812
- Bertscorer-f1: 0.3202
- Sacrebleu-score: 5.9410
- Sacrebleu-precisions: [92.24641734333713, 84.24354361048307, 78.78523204758982, 75.43428275229601]
- Bleu-bp: 0.0721

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0003
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
| nan           | 1.0   | 4772 | 0.1294          | 19.0    | 0.5827       | 0.0812       | 0.3202        | 5.9410          | [92.24641734333713, 84.24354361048307, 78.78523204758982, 75.43428275229601] | 0.0721  |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
