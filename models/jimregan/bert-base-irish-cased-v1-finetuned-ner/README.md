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
- name: bert-base-irish-cased-v1-finetuned-ner
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
      value: 0.8190601668862538
    - name: Recall
      type: recall
      value: 0.8363228699551569
    - name: F1
      type: f1
      value: 0.8276015087641446
    - name: Accuracy
      type: accuracy
      value: 0.9306559069156423
widget:
- text: "Saolaíodh Pádraic Ó Conaire i nGaillimh sa bhliain 1882."
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-irish-cased-v1-finetuned-ner

This model is a fine-tuned version of [DCU-NLP/bert-base-irish-cased-v1](https://huggingface.co/DCU-NLP/bert-base-irish-cased-v1) on the wikiann dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2468
- Precision: 0.8191
- Recall: 0.8363
- F1: 0.8276
- Accuracy: 0.9307

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
| No log        | 1.0   | 63   | 0.4902          | 0.5579    | 0.5269 | 0.5420 | 0.8458   |
| No log        | 2.0   | 126  | 0.3227          | 0.7169    | 0.7417 | 0.7291 | 0.8991   |
| No log        | 3.0   | 189  | 0.2720          | 0.7895    | 0.7839 | 0.7867 | 0.9186   |
| No log        | 4.0   | 252  | 0.2585          | 0.8128    | 0.8296 | 0.8211 | 0.9264   |
| No log        | 5.0   | 315  | 0.2468          | 0.8191    | 0.8363 | 0.8276 | 0.9307   |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
