---
language:
- en
license: mit
tags:
- generated_from_trainer
- deberta-v3
datasets:
- glue
metrics:
- accuracy
- f1
model-index:
- name: deberta-v3-small
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE MRPC
      type: glue
      args: mrpc
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8921568627450981
    - name: F1
      type: f1
      value: 0.9233449477351917
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# DeBERTa v3 (small) fine-tuned on MRPC

This model is a fine-tuned version of [microsoft/deberta-v3-small](https://huggingface.co/microsoft/deberta-v3-small) on the GLUE MRPC dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2787
- Accuracy: 0.8922
- F1: 0.9233
- Combined Score: 0.9078

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 3e-05
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10.0

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Combined Score |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:--------------:|
| No log        | 1.0   | 230  | 0.2787          | 0.8922   | 0.9233 | 0.9078         |
| No log        | 2.0   | 460  | 0.3651          | 0.875    | 0.9137 | 0.8944         |
| No log        | 3.0   | 690  | 0.5238          | 0.8799   | 0.9179 | 0.8989         |
| No log        | 4.0   | 920  | 0.4712          | 0.8946   | 0.9222 | 0.9084         |
| 0.2147        | 5.0   | 1150 | 0.5704          | 0.8946   | 0.9262 | 0.9104         |
| 0.2147        | 6.0   | 1380 | 0.5697          | 0.8995   | 0.9284 | 0.9140         |
| 0.2147        | 7.0   | 1610 | 0.6651          | 0.8922   | 0.9214 | 0.9068         |
| 0.2147        | 8.0   | 1840 | 0.6726          | 0.8946   | 0.9239 | 0.9093         |
| 0.0183        | 9.0   | 2070 | 0.7250          | 0.8848   | 0.9177 | 0.9012         |
| 0.0183        | 10.0  | 2300 | 0.7093          | 0.8922   | 0.9223 | 0.9072         |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
