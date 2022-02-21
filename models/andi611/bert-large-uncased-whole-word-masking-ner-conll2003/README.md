---
language:
- en
license: apache-2.0
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
- name: bert-large-uncased-whole-word-masking-ner-conll2003
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
      value: 0.9886888970085945
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-uncased-whole-word-masking-ner-conll2003

This model is a fine-tuned version of [bert-large-uncased-whole-word-masking](https://huggingface.co/bert-large-uncased-whole-word-masking) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0592
- Precision: 0.9527
- Recall: 0.9569
- F1: 0.9548
- Accuracy: 0.9887

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
- train_batch_size: 4
- eval_batch_size: 1
- seed: 42
- gradient_accumulation_steps: 4
- total_train_batch_size: 16
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.4071        | 1.0   | 877  | 0.0584          | 0.9306    | 0.9418 | 0.9362 | 0.9851   |
| 0.0482        | 2.0   | 1754 | 0.0594          | 0.9362    | 0.9491 | 0.9426 | 0.9863   |
| 0.0217        | 3.0   | 2631 | 0.0550          | 0.9479    | 0.9584 | 0.9531 | 0.9885   |
| 0.0103        | 4.0   | 3508 | 0.0592          | 0.9527    | 0.9569 | 0.9548 | 0.9887   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.8.1+cu111
- Datasets 1.8.0
- Tokenizers 0.10.3
