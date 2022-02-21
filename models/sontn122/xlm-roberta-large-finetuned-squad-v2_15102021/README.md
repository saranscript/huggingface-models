---
license: mit
tags:
- generated_from_trainer
datasets:
- squad_v2
model-index:
- name: xlm-roberta-large-finetuned-squad-v2_15102021
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-large-finetuned-squad-v2_15102021

This model is a fine-tuned version of [xlm-roberta-large](https://huggingface.co/xlm-roberta-large) on the squad_v2 dataset.
It achieves the following results on the evaluation set:
- eval_loss: 17.5548
- eval_runtime: 168.7788
- eval_samples_per_second: 23.368
- eval_steps_per_second: 5.842
- epoch: 8.0
- step: 7600

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- gradient_accumulation_steps: 8
- total_train_batch_size: 32
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.13.1
- Tokenizers 0.10.3
