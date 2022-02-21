---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
metrics:
- f1
model-index:
- name: text-to-sparql-t5-small-2021-10-17_18-47
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metrics:
    - name: F1
      type: f1
      value: 0.2345714420080185
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-small-2021-10-17_18-47

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5258
- Gen Len: 19.0
- P: 0.4582
- R: 0.0278
- F1: 0.2346
- Score: 3.5848
- Bleu-precisions: [82.57739877107295, 62.13358857503344, 48.43062944877681, 41.90172321318059]
- Bleu-bp: 0.0631

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
| 0.7575        | 1.0   | 4807 | 0.5258          | 19.0    | 0.4582 | 0.0278 | 0.2346 | 3.5848 | [82.57739877107295, 62.13358857503344, 48.43062944877681, 41.90172321318059] | 0.0631  |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
