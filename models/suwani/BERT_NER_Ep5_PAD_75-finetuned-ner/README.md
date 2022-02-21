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
- name: BERT_NER_Ep5_PAD_75-finetuned-ner
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BERT_NER_Ep5_PAD_75-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3504
- Precision: 0.6469
- Recall: 0.7246
- F1: 0.6835
- Accuracy: 0.9013

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 288  | 0.3695          | 0.5799    | 0.6200 | 0.5993 | 0.8792   |
| 0.4695        | 2.0   | 576  | 0.3443          | 0.5823    | 0.7252 | 0.6460 | 0.8862   |
| 0.4695        | 3.0   | 864  | 0.3189          | 0.6407    | 0.7030 | 0.6704 | 0.8978   |
| 0.2184        | 4.0   | 1152 | 0.3458          | 0.6383    | 0.7335 | 0.6826 | 0.8980   |
| 0.2184        | 5.0   | 1440 | 0.3504          | 0.6469    | 0.7246 | 0.6835 | 0.9013   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.12.1
- Tokenizers 0.10.3
