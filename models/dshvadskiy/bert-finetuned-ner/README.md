---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- conll2002
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: bert-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: conll2002
      type: conll2002
      args: es
    metrics:
    - name: Precision
      type: precision
      value: 0.7394396551724138
    - name: Recall
      type: recall
      value: 0.7883731617647058
    - name: F1
      type: f1
      value: 0.7631227758007118
    - name: Accuracy
      type: accuracy
      value: 0.9655744705631151
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-finetuned-ner

This model is a fine-tuned version of [bert-base-cased](https://huggingface.co/bert-base-cased) on the conll2002 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1458
- Precision: 0.7394
- Recall: 0.7884
- F1: 0.7631
- Accuracy: 0.9656

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1047        | 1.0   | 1041 | 0.1516          | 0.7173    | 0.7505 | 0.7335 | 0.9602   |
| 0.068         | 2.0   | 2082 | 0.1280          | 0.7470    | 0.7888 | 0.7673 | 0.9664   |
| 0.0406        | 3.0   | 3123 | 0.1458          | 0.7394    | 0.7884 | 0.7631 | 0.9656   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
