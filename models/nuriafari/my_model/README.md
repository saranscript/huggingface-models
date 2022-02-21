---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- financial_phrasebank
metrics:
- recall
- accuracy
- precision
model-index:
- name: my_model
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: financial_phrasebank
      type: financial_phrasebank
      args: sentences_50agree
    metrics:
    - name: Recall
      type: recall
      value: 0.874936448490344
    - name: Accuracy
      type: accuracy
      value: 0.865979381443299
    - name: Precision
      type: precision
      value: 0.8280314825660291
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# my_model

This model is a fine-tuned version of [deepmind/language-perceiver](https://huggingface.co/deepmind/language-perceiver) on the financial_phrasebank dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3732
- Recall: 0.8749
- Accuracy: 0.8660
- Precision: 0.8280

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
- distributed_type: tpu
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Recall | Accuracy | Precision |
|:-------------:|:-----:|:----:|:---------------:|:------:|:--------:|:---------:|
| 0.1421        | 1.0   | 273  | 0.3732          | 0.8749 | 0.8660   | 0.8280    |
| 0.1036        | 2.0   | 546  | 0.3732          | 0.8749 | 0.8660   | 0.8280    |
| 0.1836        | 3.0   | 819  | 0.3732          | 0.8749 | 0.8660   | 0.8280    |
| 0.0423        | 4.0   | 1092 | 0.3732          | 0.8749 | 0.8660   | 0.8280    |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.9.0+cu102
- Datasets 1.17.0
- Tokenizers 0.10.3
