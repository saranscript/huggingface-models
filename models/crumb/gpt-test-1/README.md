---
tags:
- generated_from_trainer
datasets:
- null
model-index:
- name: gpt-test-1
  results:
  - task:
      name: Causal Language Modeling
      type: text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# gpt-test-1

This model is a fine-tuned version of [crumb/gpt-test-1](https://huggingface.co/crumb/gpt-test-1) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 6.2516

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
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 6.081         | 1.0   | 2334 | 6.2516          |
| 6.1021        | 2.0   | 4668 | 6.2516          |
| 6.0858        | 3.0   | 7002 | 6.2516          |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
