---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: electra-small-discriminator-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann
      type: wikiann
      args: en
    metrics:
    - name: Precision
      type: precision
      value: 0.7330965535385425
    - name: Recall
      type: recall
      value: 0.7542632861138681
    - name: F1
      type: f1
      value: 0.7435293071244329
    - name: Accuracy
      type: accuracy
      value: 0.8883011190233978
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# electra-small-discriminator-finetuned-ner

This model is a fine-tuned version of [google/electra-small-discriminator](https://huggingface.co/google/electra-small-discriminator) on the wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3685
- Precision: 0.7331
- Recall: 0.7543
- F1: 0.7435
- Accuracy: 0.8883

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

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.5465        | 1.0   | 1250 | 0.4158          | 0.6932    | 0.7201 | 0.7064 | 0.8735   |
| 0.4037        | 2.0   | 2500 | 0.3817          | 0.7191    | 0.7470 | 0.7328 | 0.8828   |
| 0.3606        | 3.0   | 3750 | 0.3685          | 0.7331    | 0.7543 | 0.7435 | 0.8883   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
