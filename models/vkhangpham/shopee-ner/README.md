---
tags:
- generated_from_trainer
metrics:
- precision
- recall
- f1
- accuracy
model-index:
- name: shopee-ner
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# shopee-ner

This model is a fine-tuned version of [cahya/xlm-roberta-base-indonesian-NER](https://huggingface.co/cahya/xlm-roberta-base-indonesian-NER) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2046
- Precision: 0.7666
- Recall: 0.8666
- F1: 0.8135
- Accuracy: 0.9320

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
- num_epochs: 2

### Training results

| Training Loss | Epoch | Step  | Validation Loss | Precision | Recall | F1     | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:---------:|:------:|:------:|:--------:|
| 0.2282        | 1.0   | 33750 | 0.2174          | 0.7443    | 0.8506 | 0.7939 | 0.9253   |
| 0.1983        | 2.0   | 67500 | 0.2046          | 0.7666    | 0.8666 | 0.8135 | 0.9320   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.1
- Tokenizers 0.10.3
