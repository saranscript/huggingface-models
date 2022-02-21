---
license: mit
tags:
- generated_from_trainer
datasets:
- marker-associations-binary-base
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: marker-associations-binary-base
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: marker-associations-binary-base
      type: marker-associations-binary-base
    metrics:
    - name: Precision
      type: precision
      value: 0.7981651376146789
    - name: Recall
      type: recall
      value: 0.9560439560439561
    - name: F1
      type: f1
      value: 0.87
    - name: Accuracy
      type: accuracy
      value: 0.8884120171673819
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# marker-associations-binary-base

This model is a fine-tuned version of [microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext](https://huggingface.co/microsoft/BiomedNLP-PubMedBERT-base-uncased-abstract-fulltext) on the marker-associations-binary-base dataset.
It achieves the following results on the evaluation set:

### Gene Results
- Precision = 0.808
- Recall = 0.940
- F1 = 0.869
- Accuracy = 0.862
- AUC = 0.944

### Chemical Results
- Precision = 0.774
- Recall = 1.0
- F1 = 0.873
- Accuracy = 0.926
- AUC = 0.964

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 1
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 15

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy | Auc    |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|:------:|
| No log        | 1.0   | 88   | 0.3266          | 0.8191    | 0.8462 | 0.8324 | 0.8670   | 0.9313 |
| No log        | 2.0   | 176  | 0.3335          | 0.7870    | 0.9341 | 0.8543 | 0.8755   | 0.9465 |
| No log        | 3.0   | 264  | 0.4243          | 0.7982    | 0.9560 | 0.87   | 0.8884   | 0.9516 |
| No log        | 4.0   | 352  | 0.5388          | 0.825     | 0.7253 | 0.7719 | 0.8326   | 0.9384 |
| No log        | 5.0   | 440  | 0.7101          | 0.8537    | 0.7692 | 0.8092 | 0.8584   | 0.9416 |
| 0.1824        | 6.0   | 528  | 0.6175          | 0.8242    | 0.8242 | 0.8242 | 0.8627   | 0.9478 |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Tokenizers 0.10.3
