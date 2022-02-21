---
language:
- en
license: mit
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: deberta-v3-small
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE QNLI
      type: glue
      args: qnli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9150649826102873
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# DeBERTa-v3-small fine-tuned on QNLI

This model is a fine-tuned version of [microsoft/deberta-v3-small](https://huggingface.co/microsoft/deberta-v3-small) on the GLUE QNLI dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2143
- Accuracy: 0.9151

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
- num_epochs: 5.0

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.2823        | 1.0   | 6547  | 0.2143          | 0.9151   |
| 0.1996        | 2.0   | 13094 | 0.2760          | 0.9103   |
| 0.1327        | 3.0   | 19641 | 0.3293          | 0.9169   |
| 0.0811        | 4.0   | 26188 | 0.4278          | 0.9193   |
| 0.05          | 5.0   | 32735 | 0.5110          | 0.9176   |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
