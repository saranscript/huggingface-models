---
license: apache-2.0
tags:
- generated_from_keras_callback
model-index:
- name: BERT_Tweet_Sentiment_10k
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# BERT_Tweet_Sentiment_10k

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.3891
- Train Accuracy: 0.8273
- Validation Loss: 0.4749
- Validation Accuracy: 0.8073
- Epoch: 0

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: {'name': 'Adam', 'clipnorm': 1.0, 'learning_rate': 3e-05, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-08, 'amsgrad': False}
- training_precision: float32

### Training results

| Train Loss | Train Accuracy | Validation Loss | Validation Accuracy | Epoch |
|:----------:|:--------------:|:---------------:|:-------------------:|:-----:|
| 0.3891     | 0.8273         | 0.4749          | 0.8073              | 0     |


### Framework versions

- Transformers 4.16.2
- TensorFlow 2.8.0
- Tokenizers 0.11.0
