---
tags:
- generated_from_trainer
datasets:
- klue
metrics:
- f1
model_index:
- name: bert-base-finetuned-ynat
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: klue
      type: klue
      args: ynat
    metric:
      name: F1
      type: f1
      value: 0.8699556378491373
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-finetuned-ynat

This model is a fine-tuned version of [klue/bert-base](https://huggingface.co/klue/bert-base) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3741
- F1: 0.8700

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
- train_batch_size: 256
- eval_batch_size: 256
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | F1     |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| No log        | 1.0   | 179  | 0.4458          | 0.8516 |
| No log        | 2.0   | 358  | 0.3741          | 0.8700 |
| 0.385         | 3.0   | 537  | 0.3720          | 0.8693 |
| 0.385         | 4.0   | 716  | 0.3744          | 0.8689 |
| 0.385         | 5.0   | 895  | 0.3801          | 0.8695 |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
