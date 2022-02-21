---
language:
- de
license: mit
widget:
 - text: |
     Philipp ist 26 Jahre alt und lebt in Nürnberg, Deutschland. Derzeit arbeitet er als Machine Learning Engineer und Tech Lead bei Hugging Face, um künstliche Intelligenz durch Open Source und Open Science zu demokratisieren.
datasets:
- germaner
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: gbert-base-germaner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: germaner
      type: germaner
      args: default
    metrics:
    - name: precision
      type: precision
      value: 0.8520523797532108
    - name: recall
      type: recall
      value: 0.8754204398447607
    - name: f1
      type: f1
      value: 0.8635783563042368
    - name: accuracy
      type: accuracy
      value: 0.976147969774973
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# gbert-base-germaner

This model is a fine-tuned version of [deepset/gbert-base](https://huggingface.co/deepset/gbert-base) on the germaner dataset.
It achieves the following results on the evaluation set:
- precision: 0.8521
- recall: 0.8754
- f1: 0.8636
- accuracy: 0.9761

If you want to learn how to fine-tune BERT yourself using Keras and Tensorflow check out this blog post: 

https://www.philschmid.de/huggingface-transformers-keras-tf

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- num_train_epochs: 5
- train_batch_size: 16
- eval_batch_size: 32
- learning_rate: 2e-05
- weight_decay_rate: 0.01
- num_warmup_steps: 0
- fp16: True

### Framework versions

- Transformers 4.14.1
- Datasets 1.16.1
- Tokenizers 0.10.3
