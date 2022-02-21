---
license: apache-2.0
language: ga
tags:
- generated_from_trainer
- irish
datasets:
- wikiann
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: electra-base-irish-cased-discriminator-v1-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: wikiann
      type: wikiann
      args: ga
    metrics:
    - name: Precision
      type: precision
      value: 0.5413922859830668
    - name: Recall
      type: recall
      value: 0.5161434977578475
    - name: F1
      type: f1
      value: 0.5284664830119375
    - name: Accuracy
      type: accuracy
      value: 0.8419817960026273
widget:
- text: "Saolaíodh Pádraic Ó Conaire i nGaillimh sa bhliain 1882."
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# electra-base-irish-cased-discriminator-v1-finetuned-ner

This model is a fine-tuned version of [DCU-NLP/electra-base-irish-cased-generator-v1](https://huggingface.co/DCU-NLP/electra-base-irish-cased-generator-v1) on the wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6654
- Precision: 0.5414
- Recall: 0.5161
- F1: 0.5285
- Accuracy: 0.8420

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

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 63   | 1.3231          | 0.1046    | 0.0417 | 0.0596 | 0.5449   |
| No log        | 2.0   | 126  | 0.9710          | 0.3879    | 0.3359 | 0.3600 | 0.7486   |
| No log        | 3.0   | 189  | 0.7723          | 0.4713    | 0.4457 | 0.4582 | 0.8152   |
| No log        | 4.0   | 252  | 0.6892          | 0.5257    | 0.4910 | 0.5078 | 0.8347   |
| No log        | 5.0   | 315  | 0.6654          | 0.5414    | 0.5161 | 0.5285 | 0.8420   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
