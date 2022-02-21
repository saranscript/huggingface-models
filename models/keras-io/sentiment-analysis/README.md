---
license: apache-2.0
tags:
- generated_from_keras_callback
model-index:
- name: keras-io/sentiment-analysis
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# keras-io/sentiment-analysis

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.6865
- Validation Loss: 0.7002
- Train Accuracy: 0.4908
- Epoch: 4

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: {'name': 'Adam', 'learning_rate': 1e-04, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-07, 'amsgrad': False}
- training_precision: float32

### Training results

| Train Loss | Validation Loss | Train Accuracy | Epoch |
|:----------:|:---------------:|:--------------:|:-----:|
| 0.6865     | 0.6975          | 0.4908         | 0     |
| 0.6865     | 0.6973          | 0.4908         | 1     |
| 0.6865     | 0.6976          | 0.4908         | 2     |
| 0.6865     | 0.6975          | 0.4908         | 3     |
| 0.6865     | 0.7002          | 0.4908         | 4     |


### Framework versions

- Transformers 4.16.2
- TensorFlow 2.7.0
- Datasets 1.18.2
- Tokenizers 0.11.0
