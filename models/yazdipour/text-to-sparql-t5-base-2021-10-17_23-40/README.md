---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
metrics:
- f1
model-index:
- name: text-to-sparql-t5-base-2021-10-17_23-40
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    metrics:
    - name: F1
      type: f1
      value: 0.2649857699871063
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# text-to-sparql-t5-base-2021-10-17_23-40

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2645
- Gen Len: 19.0
- P: 0.5125
- R: 0.0382
- F1: 0.2650
- Score: 5.1404
- Bleu-precisions: [88.49268497650789, 75.01025204252232, 66.60779038484033, 63.18383699935422]
- Bleu-bp: 0.0707

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
| 0.3513        | 1.0   | 4807 | 0.2645          | 19.0    | 0.5125 | 0.0382 | 0.2650 | 5.1404 | [88.49268497650789, 75.01025204252232, 66.60779038484033, 63.18383699935422] | 0.0707  |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu111
- Datasets 1.13.3
- Tokenizers 0.10.3
