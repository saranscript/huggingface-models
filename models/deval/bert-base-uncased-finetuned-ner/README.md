---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- x_glue
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: bert-base-uncased-finetuned-ner
  results:
  - task:
      name: Token Classification
      type: token-classification
    dataset:
      name: x_glue
      type: x_glue
      args: ner
    metrics:
    - name: Precision
      type: precision
      value: 0.09187560910782316
    - name: Recall
      type: recall
      value: 0.1248795761078998
    - name: F1
      type: f1
      value: 0.10586493798172632
    - name: Accuracy
      type: accuracy
      value: 0.492660102891609
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-finetuned-ner

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the x_glue dataset.
It achieves the following results on the evaluation set:
- Loss: 2.7979
- Precision: 0.0919
- Recall: 0.1249
- F1: 0.1059
- Accuracy: 0.4927

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.1773        | 1.0   | 878  | 1.7953          | 0.1025    | 0.1352 | 0.1166 | 0.5058   |
| 0.0397        | 2.0   | 1756 | 2.0827          | 0.0906    | 0.1230 | 0.1043 | 0.4888   |
| 0.022         | 3.0   | 2634 | 2.8677          | 0.0864    | 0.1260 | 0.1025 | 0.4098   |
| 0.0126        | 4.0   | 3512 | 2.8584          | 0.0848    | 0.1201 | 0.0994 | 0.4424   |
| 0.0085        | 5.0   | 4390 | 2.7979          | 0.0919    | 0.1249 | 0.1059 | 0.4927   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
