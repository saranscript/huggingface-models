---
language:
- fr
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: jplu-wikiann
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann
      type: wikiann
      args: default
    metrics:
    - name: precision
      type: precision
      value: 0.897994120055078
    - name: recall
      type: recall
      value: 0.9097421203438395
    - name: f1
      type: f1
      value: 0.9038299466242158
    - name: accuracy
      type: accuracy
      value: 0.9464171271196716
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# jplu-wikiann

This model is a fine-tuned version of [jplu/tf-camembert-base](https://huggingface.co/jplu/tf-camembert-base) on the wikiann dataset.
It achieves the following results on the evaluation set:
- precision: 0.8980
- recall: 0.9097
- f1: 0.9038
- accuracy: 0.9464

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

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
