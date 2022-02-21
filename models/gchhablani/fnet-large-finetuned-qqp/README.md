---
language:
- en
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
- f1
model-index:
- name: fnet-large-finetuned-qqp
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: GLUE QQP
      type: glue
      args: qqp
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8943111550828593
    - name: F1
      type: f1
      value: 0.8556565212985171
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# fnet-large-finetuned-qqp

This model is a fine-tuned version of [google/fnet-large](https://huggingface.co/google/fnet-large) on the GLUE QQP dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5515
- Accuracy: 0.8943
- F1: 0.8557
- Combined Score: 0.8750

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
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3.0

### Training results

| Training Loss | Epoch | Step   | Validation Loss | Accuracy | F1     | Combined Score |
|:-------------:|:-----:|:------:|:---------------:|:--------:|:------:|:--------------:|
| 0.4574        | 1.0   | 90962  | 0.4946          | 0.8694   | 0.8297 | 0.8496         |
| 0.3387        | 2.0   | 181924 | 0.4745          | 0.8874   | 0.8437 | 0.8655         |
| 0.2029        | 3.0   | 272886 | 0.5515          | 0.8943   | 0.8557 | 0.8750         |


### Framework versions

- Transformers 4.11.0.dev0
- Pytorch 1.9.0
- Datasets 1.12.1
- Tokenizers 0.10.3
