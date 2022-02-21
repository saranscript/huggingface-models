---
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: xlm-roberta-large-finetuned-squad
  results:
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: squad
      type: squad
      args: default
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlm-roberta-large-finetuned-squad

This model is a fine-tuned version of [xlm-roberta-large](https://huggingface.co/xlm-roberta-large) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0350

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
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 1.6093        | 1.0   | 620  | 1.0023          |
| 0.849         | 2.0   | 1240 | 0.9449          |
| 0.6693        | 3.0   | 1860 | 1.0350          |


### Framework versions

- Transformers 4.10.0
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
