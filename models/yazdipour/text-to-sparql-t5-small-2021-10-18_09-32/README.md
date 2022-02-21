---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
metrics:
- f1
model-index:
- name: text-to-sparql-t5-small-2021-10-18_09-32
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metrics:
    - name: F1
      type: f1
      value: 0.26458749175071716
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-small-2021-10-18_09-32

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5119
- Gen Len: 19.0
- P: 0.4884
- R: 0.0583
- F1: 0.2646
- Score: 3.5425
- Bleu-precisions: [82.80295919500207, 62.695879280325016, 50.2215675749897, 44.03052700138759]
- Bleu-bp: 0.0609

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

| Training Loss | Epoch | Step | Validation Loss | Gen Len | P      | R      | F1     | Score  | Bleu-precisions                                                              | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:------:|:------:|:------:|:----------------------------------------------------------------------------:|:-------:|
| 0.7088        | 1.0   | 4772 | 0.5119          | 19.0    | 0.4884 | 0.0583 | 0.2646 | 3.5425 | [82.80295919500207, 62.695879280325016, 50.2215675749897, 44.03052700138759] | 0.0609  |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
