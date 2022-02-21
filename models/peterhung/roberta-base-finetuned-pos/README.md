---
license: mit
tags:
- generated_from_trainer
datasets:
- conll2003
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: roberta-base-finetuned-pos
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9318523518762849
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-finetuned-pos

This model is a fine-tuned version of [roberta-base](https://huggingface.co/roberta-base) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2951
- Precision: 0.9257
- Recall: 0.9295
- F1: 0.9276
- Accuracy: 0.9319

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
| 0.6314        | 1.0   | 878  | 0.3339          | 0.9175    | 0.9216 | 0.9195 | 0.9251   |
| 0.2203        | 2.0   | 1756 | 0.3039          | 0.9232    | 0.9254 | 0.9243 | 0.9298   |
| 0.1843        | 3.0   | 2634 | 0.2951          | 0.9257    | 0.9295 | 0.9276 | 0.9319   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
