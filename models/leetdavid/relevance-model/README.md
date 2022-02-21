---
license: apache-2.0
tags:
- generated_from_keras_callback
model-index:
- name: relevance-model
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# relevance-model

This model is a fine-tuned version of [hfl/chinese-roberta-wwm-ext](https://huggingface.co/hfl/chinese-roberta-wwm-ext) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.3134
- Train Binary Accuracy: 0.8773
- Validation Loss: 0.3633
- Validation Binary Accuracy: 0.8541
- Epoch: 2

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: {'name': 'Adam', 'learning_rate': 5e-05, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-07, 'amsgrad': False}
- training_precision: float32

### Training results

| Train Loss | Train Binary Accuracy | Validation Loss | Validation Binary Accuracy | Epoch |
|:----------:|:---------------------:|:---------------:|:--------------------------:|:-----:|
| 0.3980     | 0.8289                | 0.3739          | 0.8541                     | 0     |
| 0.3446     | 0.8606                | 0.3614          | 0.8505                     | 1     |
| 0.3134     | 0.8773                | 0.3633          | 0.8541                     | 2     |


### Framework versions

- Transformers 4.16.0
- TensorFlow 2.7.0
- Datasets 1.18.1
- Tokenizers 0.11.0
