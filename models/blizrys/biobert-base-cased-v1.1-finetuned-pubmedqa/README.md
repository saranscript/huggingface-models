---
tags:
- generated_from_trainer
datasets:
- null
metrics:
- accuracy
model-index:
- name: biobert-base-cased-v1.1-finetuned-pubmedqa
  results:
  - task:
      name: Text Classification
      type: text-classification
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.5
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-base-cased-v1.1-finetuned-pubmedqa

This model is a fine-tuned version of [dmis-lab/biobert-base-cased-v1.1](https://huggingface.co/dmis-lab/biobert-base-cased-v1.1) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3182
- Accuracy: 0.5

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 57   | 0.8591          | 0.58     |
| No log        | 2.0   | 114  | 0.9120          | 0.58     |
| No log        | 3.0   | 171  | 0.8159          | 0.62     |
| No log        | 4.0   | 228  | 1.1651          | 0.54     |
| No log        | 5.0   | 285  | 1.2350          | 0.6      |
| No log        | 6.0   | 342  | 1.5563          | 0.68     |
| No log        | 7.0   | 399  | 2.0233          | 0.58     |
| No log        | 8.0   | 456  | 2.2054          | 0.5      |
| 0.4463        | 9.0   | 513  | 2.2434          | 0.5      |
| 0.4463        | 10.0  | 570  | 2.3182          | 0.5      |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
