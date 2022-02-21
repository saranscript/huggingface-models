---
tags:
- generated_from_trainer
model-index:
- name: sparql-qald9-t5-base-2021-10-19_23-02
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sparql-qald9-t5-base-2021-10-19_23-02

This model is a fine-tuned version of [yazdipour/text-to-sparql-t5-base-2021-10-19_15-35_lastDS](https://huggingface.co/yazdipour/text-to-sparql-t5-base-2021-10-19_15-35_lastDS) on the None dataset.

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

| Training Loss | Epoch | Step | Validation Loss | Gen Len | P      | R      | F1     | Bleu-score | Bleu-precisions                                                               | Bleu-bp |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:------:|:------:|:----------:|:-----------------------------------------------------------------------------:|:-------:|
| No log        | 1.0   | 51   | 1.8300          | 19.0    | 0.3640 | 0.0346 | 0.1943 | 10.0358    | [72.88988261598658, 50.27455765710799, 35.93015446608462, 28.454070201643017] | 0.2281  |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
