---
license: mit
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model_index:
- name: bert-large-pt-archive
  results:
  - task:
      name: Token Classification
      type: token-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9766762474673703
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-large-pt-archive

This model is a fine-tuned version of [neuralmind/bert-large-portuguese-cased](https://huggingface.co/neuralmind/bert-large-portuguese-cased) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0869
- Precision: 0.9280
- Recall: 0.9541
- F1: 0.9409
- Accuracy: 0.9767

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
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.0665        | 1.0   | 765  | 0.1020          | 0.8928    | 0.9566 | 0.9236 | 0.9696   |
| 0.0392        | 2.0   | 1530 | 0.0781          | 0.9229    | 0.9586 | 0.9404 | 0.9757   |
| 0.0201        | 3.0   | 2295 | 0.0809          | 0.9278    | 0.9550 | 0.9412 | 0.9767   |
| 0.0152        | 4.0   | 3060 | 0.0869          | 0.9280    | 0.9541 | 0.9409 | 0.9767   |


### Framework versions

- Transformers 4.10.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.10.2
- Tokenizers 0.10.3
