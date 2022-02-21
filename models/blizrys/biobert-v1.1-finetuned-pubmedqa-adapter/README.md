---
tags:
- generated_from_trainer
datasets:
- null
metrics:
- accuracy
model_index:
- name: biobert-v1.1-finetuned-pubmedqa-adapter
  results:
  - task:
      name: Text Classification
      type: text-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.48
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# biobert-v1.1-finetuned-pubmedqa-adapter

This model is a fine-tuned version of [dmis-lab/biobert-v1.1](https://huggingface.co/dmis-lab/biobert-v1.1) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 2.0910
- Accuracy: 0.48

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.003
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 57   | 0.9848          | 0.58     |
| No log        | 2.0   | 114  | 0.8537          | 0.58     |
| No log        | 3.0   | 171  | 0.9565          | 0.42     |
| No log        | 4.0   | 228  | 0.9659          | 0.56     |
| No log        | 5.0   | 285  | 0.9763          | 0.6      |
| No log        | 6.0   | 342  | 1.0647          | 0.66     |
| No log        | 7.0   | 399  | 1.4305          | 0.6      |
| No log        | 8.0   | 456  | 2.0545          | 0.56     |
| 0.6957        | 9.0   | 513  | 2.2438          | 0.5      |
| 0.6957        | 10.0  | 570  | 2.0910          | 0.48     |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
