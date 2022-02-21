---
license: apache-2.0
tags:
- generated_from_keras_callback
model-index:
- name: importance_model
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# importance_model

This model is a fine-tuned version of [hfl/chinese-roberta-wwm-ext](https://huggingface.co/hfl/chinese-roberta-wwm-ext) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.5902
- Train Sparse Categorical Accuracy: 0.7910
- Validation Loss: 0.8534
- Validation Sparse Categorical Accuracy: 0.7372
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

| Train Loss | Train Sparse Categorical Accuracy | Validation Loss | Validation Sparse Categorical Accuracy | Epoch |
|:----------:|:---------------------------------:|:---------------:|:--------------------------------------:|:-----:|
| 0.9209     | 0.6502                            | 0.8464          | 0.7055                                 | 0     |
| 0.7112     | 0.7633                            | 0.8572          | 0.7332                                 | 1     |
| 0.5902     | 0.7910                            | 0.8534          | 0.7372                                 | 2     |


### Framework versions

- Transformers 4.16.0
- TensorFlow 2.7.0
- Datasets 1.18.1
- Tokenizers 0.11.0
