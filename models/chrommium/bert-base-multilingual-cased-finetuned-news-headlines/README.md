---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model_index:
- name: bert-base-multilingual-cased-finetuned-cola
  results:
  - task:
      name: Text Classification
      type: text-classification
    metric:
      name: Accuracy
      type: accuracy
      value: 0.9755
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-multilingual-cased-finetuned-cola

This model is a fine-tuned version of [bert-base-multilingual-cased](https://huggingface.co/bert-base-multilingual-cased) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.1729
- Accuracy: 0.9755

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

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.5119        | 1.0   | 625  | 0.2386          | 0.922    |
| 0.2536        | 2.0   | 1250 | 0.2055          | 0.949    |
| 0.1718        | 3.0   | 1875 | 0.1733          | 0.969    |
| 0.0562        | 4.0   | 2500 | 0.1661          | 0.974    |
| 0.0265        | 5.0   | 3125 | 0.1729          | 0.9755   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
