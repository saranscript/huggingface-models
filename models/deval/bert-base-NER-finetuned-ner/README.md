---
license: mit
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
- name: bert-base-NER-finetuned-ner
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
      value: 0.2273838630806846
    - name: Recall
      type: recall
      value: 0.11185727172496743
    - name: F1
      type: f1
      value: 0.14994961370507223
    - name: Accuracy
      type: accuracy
      value: 0.8485324947589099
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-NER-finetuned-ner

This model is a fine-tuned version of [dslim/bert-base-NER](https://huggingface.co/dslim/bert-base-NER) on the x_glue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4380
- Precision: 0.2274
- Recall: 0.1119
- F1: 0.1499
- Accuracy: 0.8485

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
| 0.0822        | 1.0   | 878  | 1.1648          | 0.2068    | 0.1101 | 0.1437 | 0.8471   |
| 0.0102        | 2.0   | 1756 | 1.2697          | 0.2073    | 0.1110 | 0.1445 | 0.8447   |
| 0.0049        | 3.0   | 2634 | 1.3945          | 0.2006    | 0.1073 | 0.1399 | 0.8368   |
| 0.0025        | 4.0   | 3512 | 1.3994          | 0.2243    | 0.1126 | 0.1499 | 0.8501   |
| 0.0011        | 5.0   | 4390 | 1.4380          | 0.2274    | 0.1119 | 0.1499 | 0.8485   |


### Framework versions

- Transformers 4.10.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
