---
tags:
- generated_from_trainer
datasets:
- conll2003
model_index:
- name: distilbert-base-uncased-squad2-with-ner-with-neg-with-multi-with-repeat
  results:
  - task:
      name: Question Answering
      type: question-answering
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-squad2-with-ner-with-neg-with-multi-with-repeat

This model is a fine-tuned version of [twmkn9/distilbert-base-uncased-squad2](https://huggingface.co/twmkn9/distilbert-base-uncased-squad2) on the conll2003 dataset.

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
- num_epochs: 5

### Training results



### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
