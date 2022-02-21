---
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
model-index:
- name: bert-base-multilingual-cased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2003
      type: conll2003
      args: conll2003
    metrics:
    - name: Precision
      type: precision
      value: 0.9489057950596412
    - name: Recall
      type: recall
      value: 0.9541033147606006
    - name: F1
      type: f1
      value: 0.9514974571482389
    - name: Accuracy
      type: accuracy
      value: 0.9879831588795976
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-multilingual-cased-finetuned-ner

This model is a fine-tuned version of [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased) on the conll2003 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0585
- Precision: 0.9489
- Recall: 0.9541
- F1: 0.9515
- Accuracy: 0.9880

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
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1739        | 1.0   | 878  | 0.0741          | 0.9246    | 0.9181 | 0.9213 | 0.9823   |
| 0.045         | 2.0   | 1756 | 0.0586          | 0.9469    | 0.9476 | 0.9472 | 0.9870   |
| 0.0213        | 3.0   | 2634 | 0.0583          | 0.9503    | 0.9510 | 0.9506 | 0.9877   |
| 0.0113        | 4.0   | 3512 | 0.0585          | 0.9489    | 0.9541 | 0.9515 | 0.9880   |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
