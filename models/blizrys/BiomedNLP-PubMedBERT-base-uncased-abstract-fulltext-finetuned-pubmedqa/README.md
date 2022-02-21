---
license: mit
tags:
- generated_from_trainer
datasets:
- null
metrics:
- accuracy
model-index:
- name: BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-pubmedqa
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.72
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-pubmedqa

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6748
- Accuracy: 0.72

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 57   | 0.8396          | 0.58     |
| No log        | 2.0   | 114  | 0.8608          | 0.58     |
| No log        | 3.0   | 171  | 0.7642          | 0.68     |
| No log        | 4.0   | 228  | 0.8196          | 0.64     |
| No log        | 5.0   | 285  | 0.6477          | 0.72     |
| No log        | 6.0   | 342  | 0.6861          | 0.72     |
| No log        | 7.0   | 399  | 0.6735          | 0.74     |
| No log        | 8.0   | 456  | 0.6516          | 0.72     |
| 0.6526        | 9.0   | 513  | 0.6707          | 0.72     |
| 0.6526        | 10.0  | 570  | 0.6748          | 0.72     |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.0
- Tokenizers 0.10.3
