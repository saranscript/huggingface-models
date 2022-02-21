---
tags:
- generated_from_trainer
datasets:
- ncbi_disease
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: biobert_v1.1_pubmed-finetuned-ner-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: ncbi_disease
      type: ncbi_disease
      args: ncbi_disease
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9829142288061745
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert_v1.1_pubmed-finetuned-ner-finetuned-ner

This model is a fine-tuned version of [fidukm34/biobert_v1.1_pubmed-finetuned-ner](https://huggingface.co/fidukm34/biobert_v1.1_pubmed-finetuned-ner) on the ncbi_disease dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0715
- Precision: 0.8464
- Recall: 0.8872
- F1: 0.8663
- Accuracy: 0.9829

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
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 340  | 0.0715          | 0.8464    | 0.8872 | 0.8663 | 0.9829   |


### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
