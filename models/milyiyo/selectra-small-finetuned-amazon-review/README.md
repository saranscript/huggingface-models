---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- amazon_reviews_multi
metrics:
- accuracy
- f1
- precision
- recall
model-index:
- name: selectra-small-finetuned-amazon-review
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: amazon_reviews_multi
      type: amazon_reviews_multi
      args: es
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.737
    - name: F1
      type: f1
      value: 0.7437773019932409
    - name: Precision
      type: precision
      value: 0.7524857881639091
    - name: Recall
      type: recall
      value: 0.737
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# selectra-small-finetuned-amazon-review

This model is a fine-tuned version of [Recognai/selectra_small](https://huggingface.co/Recognai/selectra_small) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6279
- Accuracy: 0.737
- F1: 0.7438
- Precision: 0.7525
- Recall: 0.737

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

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:---------:|:------:|
| No log        | 0.5   | 500  | 0.7041          | 0.7178   | 0.6724 | 0.6715    | 0.7178 |
| 0.7908        | 1.0   | 1000 | 0.6365          | 0.7356   | 0.7272 | 0.7211    | 0.7356 |
| 0.7908        | 1.5   | 1500 | 0.6204          | 0.7376   | 0.7380 | 0.7387    | 0.7376 |
| 0.6358        | 2.0   | 2000 | 0.6162          | 0.7386   | 0.7377 | 0.7380    | 0.7386 |
| 0.6358        | 2.5   | 2500 | 0.6228          | 0.7274   | 0.7390 | 0.7576    | 0.7274 |
| 0.5827        | 3.0   | 3000 | 0.6188          | 0.7378   | 0.7400 | 0.7425    | 0.7378 |
| 0.5827        | 3.5   | 3500 | 0.6246          | 0.7374   | 0.7416 | 0.7467    | 0.7374 |
| 0.5427        | 4.0   | 4000 | 0.6266          | 0.7446   | 0.7452 | 0.7465    | 0.7446 |
| 0.5427        | 4.5   | 4500 | 0.6331          | 0.7392   | 0.7421 | 0.7456    | 0.7392 |
| 0.5184        | 5.0   | 5000 | 0.6279          | 0.737    | 0.7438 | 0.7525    | 0.737  |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
