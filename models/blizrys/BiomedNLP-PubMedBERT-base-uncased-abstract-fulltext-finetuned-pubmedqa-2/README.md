---
license: mit
tags:
- generated_from_trainer
datasets:
- null
metrics:
- accuracy
model-index:
- name: BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-pubmedqa-2
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.54
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-pubmedqa-2

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0005
- Accuracy: 0.54

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 57   | 1.3510          | 0.54     |
| No log        | 2.0   | 114  | 0.9606          | 0.54     |
| No log        | 3.0   | 171  | 0.9693          | 0.54     |
| No log        | 4.0   | 228  | 1.0445          | 0.54     |
| No log        | 5.0   | 285  | 1.0005          | 0.54     |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
