---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-mlm-pubmed-medterm
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-mlm-pubmed-medterm

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0000
- Rouge2 Precision: 0.985
- Rouge2 Recall: 0.7208
- Rouge2 Fmeasure: 0.8088

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
- num_epochs: 10
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Rouge2 Precision | Rouge2 Recall | Rouge2 Fmeasure |
|:-------------:|:-----:|:------:|:---------------:|:----------------:|:-------------:|:---------------:|
| 0.0018        | 1.0   | 13833  | 0.0003          | 0.985            | 0.7208        | 0.8088          |
| 0.0014        | 2.0   | 27666  | 0.0006          | 0.9848           | 0.7207        | 0.8086          |
| 0.0009        | 3.0   | 41499  | 0.0002          | 0.9848           | 0.7207        | 0.8086          |
| 0.0007        | 4.0   | 55332  | 0.0002          | 0.985            | 0.7208        | 0.8088          |
| 0.0006        | 5.0   | 69165  | 0.0001          | 0.9848           | 0.7207        | 0.8087          |
| 0.0001        | 6.0   | 82998  | 0.0002          | 0.9846           | 0.7206        | 0.8086          |
| 0.0009        | 7.0   | 96831  | 0.0001          | 0.9848           | 0.7208        | 0.8087          |
| 0.0           | 8.0   | 110664 | 0.0000          | 0.9848           | 0.7207        | 0.8087          |
| 0.0001        | 9.0   | 124497 | 0.0000          | 0.985            | 0.7208        | 0.8088          |
| 0.0           | 10.0  | 138330 | 0.0000          | 0.985            | 0.7208        | 0.8088          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
