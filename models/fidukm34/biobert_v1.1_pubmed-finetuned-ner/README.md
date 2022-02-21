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
- name: biobert_v1.1_pubmed-finetuned-ner
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
      value: 0.9827274990663513
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert_v1.1_pubmed-finetuned-ner

This model is a fine-tuned version of [monologg/biobert_v1.1_pubmed](https://huggingface.co/monologg/biobert_v1.1_pubmed) on the ncbi_disease dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0657
- Precision: 0.8338
- Recall: 0.8933
- F1: 0.8625
- Accuracy: 0.9827

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
| No log        | 1.0   | 340  | 0.0612          | 0.8268    | 0.85   | 0.8382 | 0.9806   |
| 0.0987        | 2.0   | 680  | 0.0604          | 0.8397    | 0.8848 | 0.8616 | 0.9829   |
| 0.0272        | 3.0   | 1020 | 0.0657          | 0.8338    | 0.8933 | 0.8625 | 0.9827   |


### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0
- Datasets 1.6.2
- Tokenizers 0.10.3
