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
- name: model
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# model

This model is a fine-tuned version of [google/bigbird-roberta-base](https://huggingface.co/google/bigbird-roberta-base) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 0.8112
- Precision: 0.2287
- Recall: 0.3749
- F1: 0.2841
- Accuracy: 0.7720

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2.5e-05
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.8734        | 1.0   | 1250 | 0.6992          | 0.1678    | 0.2855 | 0.2114 | 0.7718   |
| 0.6253        | 2.0   | 2500 | 0.6999          | 0.2329    | 0.3323 | 0.2739 | 0.7804   |
| 0.5002        | 3.0   | 3750 | 0.7040          | 0.2224    | 0.3729 | 0.2786 | 0.7794   |
| 0.3959        | 4.0   | 5000 | 0.7541          | 0.2279    | 0.3688 | 0.2817 | 0.7738   |
| 0.3181        | 5.0   | 6250 | 0.8112          | 0.2287    | 0.3749 | 0.2841 | 0.7720   |


### Framework versions

- Transformers 4.16.1
- Pytorch 1.10.0
- Datasets 1.18.2
- Tokenizers 0.11.0
