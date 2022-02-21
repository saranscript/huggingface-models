---
license: agpl-3.0
tags:
- generated_from_trainer
datasets:
- mim_gold_ner
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: XLMR-ENIS-finetuned-conll_ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: mim_gold_ner
      type: mim_gold_ner
      args: mim-gold-ner
    metrics:
    - name: Precision
      type: precision
      value: 0.8754622097322882
    - name: Recall
      type: recall
      value: 0.8425622775800712
    - name: F1
      type: f1
      value: 0.8586972290729725
    - name: Accuracy
      type: accuracy
      value: 0.9860744627305035
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLMR-ENIS-finetuned-conll_ner

This model is a fine-tuned version of [vesteinn/XLMR-ENIS](https://huggingface.co/vesteinn/XLMR-ENIS) on the mim_gold_ner dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0713
- Precision: 0.8755
- Recall: 0.8426
- F1: 0.8587
- Accuracy: 0.9861

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
| 0.0493        | 1.0   | 2904 | 0.0673          | 0.8588    | 0.8114 | 0.8344 | 0.9841   |
| 0.0277        | 2.0   | 5808 | 0.0620          | 0.8735    | 0.8275 | 0.8499 | 0.9855   |
| 0.0159        | 3.0   | 8712 | 0.0713          | 0.8755    | 0.8426 | 0.8587 | 0.9861   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
