---
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: biobertpt-all-finetuned-ner
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobertpt-all-finetuned-ner

This model is a fine-tuned version of [pucpr/biobertpt-all](https://huggingface.co/pucpr/biobertpt-all) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3721
- Precision: 0.0179
- Recall: 0.0149
- F1: 0.0163
- Accuracy: 0.6790

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
| No log        | 1.0   | 1    | 2.7864          | 0.0091    | 0.0448 | 0.0152 | 0.3339   |
| No log        | 2.0   | 2    | 2.5096          | 0.0097    | 0.0149 | 0.0118 | 0.6292   |
| No log        | 3.0   | 3    | 2.3721          | 0.0179    | 0.0149 | 0.0163 | 0.6790   |


### Framework versions

- Transformers 4.12.0.dev0
- Pytorch 1.9.1+cu102
- Datasets 1.13.3
- Tokenizers 0.10.3
