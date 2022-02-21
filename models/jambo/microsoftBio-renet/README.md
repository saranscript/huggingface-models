---
license: mit
tags:
- generated_from_trainer
datasets:
- renet
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-renet
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: renet
      type: renet
    metric:
      name: Accuracy
      type: accuracy
      value: 0.8640646029609691
---

# BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext-finetuned-renet

A model for detecting gene disease associations from abstracts. The model classifies as 0 for no association, or 1 for some association.

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the [RENET2](https://github.com/sujunhao/RENET2) dataset. Note that this considers only the abstract data, and not the full text information, from RENET2. 

It achieves the following results on the evaluation set:
- Loss: 0.7226
- Precision: 0.7799
- Recall: 0.8211
- F1: 0.8
- Accuracy: 0.8641
- Auc: 0.9325

## Training procedure
The abstract dataset from RENET2 was split into 85% train, 15% evaluation being grouped by PMIDs and stratified by labels. That is, no data from the same PMID was seen in multiple both the training and the evaluation set.

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 1
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5


### Framework versions

- Transformers 4.9.0.dev0
- Pytorch 1.10.0.dev20210630+cu113
- Datasets 1.8.0
- Tokenizers 0.10.3
