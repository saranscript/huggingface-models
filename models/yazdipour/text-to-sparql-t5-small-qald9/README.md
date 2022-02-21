---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: sparql-qald9-t5-small-2021-10-19_22-32
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sparql-qald9-t5-small-2021-10-19_22-32

This model is a fine-tuned version of [yazdipour/text-to-sparql-t5-small-2021-10-19_10-17_lastDS](https://huggingface.co/yazdipour/text-to-sparql-t5-small-2021-10-19_10-17_lastDS) on the None dataset.

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

| Training Loss | Epoch | Step | Validation Loss | Gen Len | P      | R      | F1     | Bleu-score | Bleu-precisions                                                                 | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:------:|:------:|:----------:|:-------------------------------------------------------------------------------:|:-------:|
| No log        | 1.0   | 51   | 2.4477          | 19.0    | 0.3797 | 0.0727 | 0.2219 | 9.3495     | [73.47751849743882, 49.595519601742375, 35.346602608098834, 26.243305279265492] | 0.2180  |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
