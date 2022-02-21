---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: all-mpnet-base-v2-finetuned-mydata
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# all-mpnet-base-v2-finetuned-mydata

This model is a fine-tuned version of [sentence-transformers/all-mpnet-base-v2](https://huggingface.co/sentence-transformers/all-mpnet-base-v2) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.0441

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

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| No log        | 1.0   | 416  | 4.5566          |
| 5.5599        | 2.0   | 832  | 3.9093          |
| 4.1188        | 3.0   | 1248 | 3.6204          |
| 3.6951        | 4.0   | 1664 | 3.4622          |
| 3.4406        | 5.0   | 2080 | 3.3143          |
| 3.4406        | 6.0   | 2496 | 3.2054          |
| 3.3001        | 7.0   | 2912 | 3.1572          |
| 3.2002        | 8.0   | 3328 | 3.0510          |
| 3.1467        | 9.0   | 3744 | 3.0717          |
| 3.0763        | 10.0  | 4160 | 3.0017          |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
