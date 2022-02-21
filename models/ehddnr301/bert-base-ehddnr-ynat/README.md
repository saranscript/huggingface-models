---
tags:
- generated_from_trainer
datasets:
- klue
metrics:
- f1
model_index:
- name: bert-base-ehddnr-ynat
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
      value: 0.8720568553403009
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-ehddnr-ynat

This model is a fine-tuned version of [klue/bert-base](https://huggingface.co/klue/bert-base) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3587
- F1: 0.8721

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
| No log        | 1.0   | 179  | 0.4398          | 0.8548 |
| No log        | 2.0   | 358  | 0.3587          | 0.8721 |
| 0.3859        | 3.0   | 537  | 0.3639          | 0.8707 |
| 0.3859        | 4.0   | 716  | 0.3592          | 0.8692 |
| 0.3859        | 5.0   | 895  | 0.3646          | 0.8717 |


### Framework versions

- Transformers 4.9.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
