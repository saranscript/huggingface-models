---
tags:
- generated_from_trainer
datasets:
- nsmc
metrics:
- accuracy
- f1
- recall
- precision
model-index:
- name: kcbert-base-finetuned-nsmc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: nsmc
      type: nsmc
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.90198
    - name: F1
      type: f1
      value: 0.9033161705233671
    - name: Recall
      type: recall
      value: 0.9095062169785088
    - name: Precision
      type: precision
      value: 0.8972098126812446
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# kcbert-base-finetuned-nsmc

This model is a fine-tuned version of [beomi/kcbert-base](https://huggingface.co/beomi/kcbert-base) on the nsmc dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4197
- Accuracy: 0.9020
- F1: 0.9033
- Recall: 0.9095
- Precision: 0.8972

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
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy | F1     | Recall | Precision |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|:------:|:------:|:---------:|
| 0.3028        | 0.32  | 3000  | 0.2994          | 0.8769   | 0.8732 | 0.8422 | 0.9066    |
| 0.2833        | 0.64  | 6000  | 0.2766          | 0.8880   | 0.8844 | 0.8512 | 0.9203    |
| 0.2719        | 0.96  | 9000  | 0.2527          | 0.8980   | 0.8981 | 0.8933 | 0.9030    |
| 0.1938        | 1.28  | 12000 | 0.2934          | 0.8969   | 0.8965 | 0.8869 | 0.9062    |
| 0.1907        | 1.6   | 15000 | 0.3141          | 0.8992   | 0.8999 | 0.9003 | 0.8996    |
| 0.1824        | 1.92  | 18000 | 0.3537          | 0.8986   | 0.8964 | 0.8711 | 0.9232    |
| 0.1261        | 2.24  | 21000 | 0.4197          | 0.9020   | 0.9033 | 0.9095 | 0.8972    |
| 0.1237        | 2.56  | 24000 | 0.4170          | 0.8995   | 0.9017 | 0.9156 | 0.8882    |
| 0.1182        | 2.88  | 27000 | 0.4165          | 0.9020   | 0.9036 | 0.9130 | 0.8945    |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.1
- Datasets 1.14.0
- Tokenizers 0.10.3
