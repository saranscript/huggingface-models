---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model-index:
- name: distilgpt2-finetuned-wikitext2
  results:
  - task:
      name: Causal Language Modeling
      type: text-generation
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilgpt2-finetuned-wikitext2

This model is a fine-tuned version of [distilgpt2](https://huggingface.co/distilgpt2) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 3.6426

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
| 3.5974        | 1.0   | 2334 | 3.6426          |
| 3.5891        | 2.0   | 4668 | 3.6426          |
| 3.572         | 3.0   | 7002 | 3.6426          |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.7.1
- Datasets 1.11.0
- Tokenizers 0.10.3
