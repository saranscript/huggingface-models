---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: BERT_NER_Ep5_PAD_50-finetuned-ner
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BERT_NER_Ep5_PAD_50-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3893
- Precision: 0.6540
- Recall: 0.7348
- F1: 0.6920
- Accuracy: 0.9006

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
- num_epochs: 7

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 288  | 0.3705          | 0.5852    | 0.6215 | 0.6028 | 0.8793   |
| 0.4885        | 2.0   | 576  | 0.3351          | 0.5925    | 0.7317 | 0.6548 | 0.8865   |
| 0.4885        | 3.0   | 864  | 0.3196          | 0.6471    | 0.7138 | 0.6788 | 0.8994   |
| 0.2172        | 4.0   | 1152 | 0.3368          | 0.6454    | 0.7323 | 0.6861 | 0.8992   |
| 0.2172        | 5.0   | 1440 | 0.3491          | 0.6507    | 0.7312 | 0.6886 | 0.9008   |
| 0.1459        | 6.0   | 1728 | 0.3833          | 0.6715    | 0.7018 | 0.6863 | 0.9013   |
| 0.1045        | 7.0   | 2016 | 0.3893          | 0.6540    | 0.7348 | 0.6920 | 0.9006   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
