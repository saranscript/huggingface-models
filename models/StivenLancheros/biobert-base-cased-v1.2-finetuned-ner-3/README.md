---
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: biobert-base-cased-v1.2-finetuned-ner-3
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-base-cased-v1.2-finetuned-ner-3

This model is a fine-tuned version of [dmis-lab/biobert-base-cased-v1.2](https://huggingface.co/dmis-lab/biobert-base-cased-v1.2) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0949
- Precision: 0.8619
- Recall: 0.8600
- F1: 0.8609
- Accuracy: 0.9822

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0562        | 1.0   | 6128  | 0.0693          | 0.8507    | 0.8034 | 0.8264 | 0.9790   |
| 0.0307        | 2.0   | 12256 | 0.0739          | 0.8527    | 0.8468 | 0.8497 | 0.9810   |
| 0.0142        | 3.0   | 18384 | 0.0895          | 0.8449    | 0.8549 | 0.8499 | 0.9804   |
| 0.0073        | 4.0   | 24512 | 0.0949          | 0.8619    | 0.8600 | 0.8609 | 0.9822   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.2
- Tokenizers 0.11.0
