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
- name: BERT_NER_Ep6_PAD_50-finetuned-ner
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BERT_NER_Ep6_PAD_50-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3741
- Precision: 0.6510
- Recall: 0.7399
- F1: 0.6926
- Accuracy: 0.9020

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
- num_epochs: 6

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 288  | 0.3648          | 0.5949    | 0.5907 | 0.5928 | 0.8792   |
| 0.4815        | 2.0   | 576  | 0.3400          | 0.5860    | 0.7390 | 0.6536 | 0.8867   |
| 0.4815        | 3.0   | 864  | 0.3217          | 0.6404    | 0.7129 | 0.6747 | 0.8992   |
| 0.2206        | 4.0   | 1152 | 0.3430          | 0.6413    | 0.7321 | 0.6837 | 0.8995   |
| 0.2206        | 5.0   | 1440 | 0.3560          | 0.6464    | 0.7377 | 0.6890 | 0.9010   |
| 0.1487        | 6.0   | 1728 | 0.3741          | 0.6510    | 0.7399 | 0.6926 | 0.9020   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
