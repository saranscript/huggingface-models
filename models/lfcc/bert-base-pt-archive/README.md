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
- name: bert-base-pt-archive
  results:
  - task:
      name: Token Classification
      type: token-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9700325118974698
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-pt-archive

This model is a fine-tuned version of [neuralmind/bert-base-portuguese-cased](https://huggingface.co/neuralmind/bert-base-portuguese-cased) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1140
- Precision: 0.9147
- Recall: 0.9483
- F1: 0.9312
- Accuracy: 0.9700

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
- num_epochs: 4

### Training results

| Training Loss | Epoch | Step | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:---------:|:------:|:------:|:--------:|
| No log        | 1.0   | 192  | 0.1438          | 0.8917    | 0.9392 | 0.9148 | 0.9633   |
| 0.2454        | 2.0   | 384  | 0.1222          | 0.8985    | 0.9417 | 0.9196 | 0.9671   |
| 0.0526        | 3.0   | 576  | 0.1098          | 0.9150    | 0.9481 | 0.9312 | 0.9698   |
| 0.0372        | 4.0   | 768  | 0.1140          | 0.9147    | 0.9483 | 0.9312 | 0.9700   |


### Framework versions

- Transformers 4.10.0.dev0
- Pytorch 1.9.0+cu111
- Datasets 1.10.2
- Tokenizers 0.10.3
