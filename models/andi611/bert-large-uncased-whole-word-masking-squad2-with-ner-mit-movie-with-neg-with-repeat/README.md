---
language:
- en
license: cc-by-4.0
tags:
- generated_from_trainer
datasets:
- squad_v2
- mit_movie
model_index:
- name: bert-large-uncased-whole-word-masking-squad2-with-ner-mit-movie-with-neg-with-repeat
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: squad_v2
      type: squad_v2
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: mit_movie
      type: mit_movie
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-uncased-whole-word-masking-squad2-with-ner-mit-movie-with-neg-with-repeat

This model is a fine-tuned version of [deepset/bert-large-uncased-whole-word-masking-squad2](https://huggingface.co/deepset/bert-large-uncased-whole-word-masking-squad2) on the squad_v2 and the mit_movie datasets.

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
- eval_batch_size: 1
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results



### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
