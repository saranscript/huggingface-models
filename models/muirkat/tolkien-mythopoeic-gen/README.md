---
license: mit
tags:
- generated_from_trainer
model-index:
- name: tolkien-mythopoeic-gen
  results:
  - task:
      name: Causal Language Modeling
      type: text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# tolkien-mythopoeic-gen

This model is a fine-tuned version of [gpt2](https://huggingface.co/gpt2) on Tolkien's mythopoeic works, namely The Silmarillion and Unfinished Tales of Numenor and Middle Earth.

It achieves the following results on the evaluation set:
- Loss: 3.5110

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 3.5732        | 1.0   | 145  | 3.5110          |
| 3.5713        | 2.0   | 290  | 3.5110          |
| 3.5718        | 3.0   | 435  | 3.5110          |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Tokenizers 0.10.3
