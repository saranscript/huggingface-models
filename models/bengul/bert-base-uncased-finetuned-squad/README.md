---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- squad_v2
model_index:
- name: bert-base-uncased-finetuned-squad
  results:
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: squad_v2
      type: squad_v2
      args: squad_v2
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-squad

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the squad_v2 dataset.
It achieves the following results on the evaluation set:
- Loss: 1.3242

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.0199        | 1.0   | 8157  | 1.0224          |
| 0.7507        | 2.0   | 16314 | 1.1812          |
| 0.5448        | 3.0   | 24471 | 1.3242          |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
