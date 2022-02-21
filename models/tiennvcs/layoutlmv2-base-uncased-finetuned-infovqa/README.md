---
license: cc-by-sa-4.0
tags:
- generated_from_trainer
model-index:
- name: layoutlmv2-base-uncased-finetuned-infovqa
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# layoutlmv2-base-uncased-finetuned-infovqa

This model is a fine-tuned version of [microsoft/layoutlmv2-base-uncased](https://huggingface.co/microsoft/layoutlmv2-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0870

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 250500
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 3.8677        | 0.16  | 500  | 3.2829          |
| 3.0395        | 0.33  | 1000 | 2.8431          |
| 2.561         | 0.49  | 1500 | 2.5633          |
| 2.41          | 0.65  | 2000 | 2.3548          |
| 2.247         | 0.82  | 2500 | 2.2983          |
| 2.1538        | 0.98  | 3000 | 2.2059          |
| 1.7           | 1.14  | 3500 | 2.2006          |
| 1.5705        | 1.31  | 4000 | 2.2736          |
| 1.604         | 1.47  | 4500 | 2.1415          |
| 1.5509        | 1.63  | 5000 | 2.0853          |
| 1.5053        | 1.79  | 5500 | 2.1389          |
| 1.4787        | 1.96  | 6000 | 2.0870          |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.8.0+cu101
- Datasets 1.14.0
- Tokenizers 0.10.3
