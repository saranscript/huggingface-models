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
- name: electra-small-finetuned-amazon-review
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: amazon_reviews_multi
      type: amazon_reviews_multi
      args: en
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.5504
    - name: F1
      type: f1
      value: 0.5457527808330634
    - name: Precision
      type: precision
      value: 0.5428695841337288
    - name: Recall
      type: recall
      value: 0.5504
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# electra-small-finetuned-amazon-review

This model is a fine-tuned version of [google/electra-small-discriminator](https://huggingface.co/google/electra-small-discriminator) on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0560
- Accuracy: 0.5504
- F1: 0.5458
- Precision: 0.5429
- Recall: 0.5504

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 3
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     | Precision | Recall |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|:---------:|:------:|
| 1.2172        | 1.0   | 1000 | 1.1014          | 0.5216   | 0.4902 | 0.4954    | 0.5216 |
| 1.0027        | 2.0   | 2000 | 1.0388          | 0.549    | 0.5471 | 0.5494    | 0.549  |
| 0.9035        | 3.0   | 3000 | 1.0560          | 0.5504   | 0.5458 | 0.5429    | 0.5504 |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
