---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- nerd
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: ner_nerd
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: nerd
      type: nerd
      args: nerd
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9391592461061087
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# ner_nerd

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the nerd dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2245
- Precision: 0.7466
- Recall: 0.7873
- F1: 0.7664
- Accuracy: 0.9392

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
- lr_scheduler_warmup_ratio: 0.1
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2843        | 1.0   | 8235  | 0.1951          | 0.7352    | 0.7824 | 0.7580 | 0.9375   |
| 0.1655        | 2.0   | 16470 | 0.1928          | 0.7519    | 0.7827 | 0.7670 | 0.9398   |
| 0.1216        | 3.0   | 24705 | 0.2119          | 0.75      | 0.7876 | 0.7684 | 0.9396   |
| 0.0881        | 4.0   | 32940 | 0.2258          | 0.7515    | 0.7896 | 0.7701 | 0.9392   |
| 0.0652        | 5.0   | 41175 | 0.2564          | 0.7518    | 0.7875 | 0.7692 | 0.9387   |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.2
