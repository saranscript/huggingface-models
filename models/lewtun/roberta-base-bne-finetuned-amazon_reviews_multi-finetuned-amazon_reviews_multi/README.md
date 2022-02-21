---
tags:
- generated_from_trainer
datasets:
- amazon_reviews_multi
metrics:
- accuracy
model_index:
- name: roberta-base-bne-finetuned-amazon_reviews_multi-finetuned-amazon_reviews_multi
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: amazon_reviews_multi
      type: amazon_reviews_multi
      args: es
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9285
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# roberta-base-bne-finetuned-amazon_reviews_multi-finetuned-amazon_reviews_multi

This model was trained from scratch on the amazon_reviews_multi dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3595
- Accuracy: 0.9285

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
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.103         | 1.0   | 1250 | 0.2864          | 0.928    |
| 0.0407        | 2.0   | 2500 | 0.3595          | 0.9285   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
