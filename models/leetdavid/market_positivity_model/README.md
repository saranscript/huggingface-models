---
license: apache-2.0
tags:
- generated_from_keras_callback
model-index:
- name: market_positivity_model
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# market_positivity_model

This model is a fine-tuned version of [hfl/chinese-roberta-wwm-ext](https://huggingface.co/hfl/chinese-roberta-wwm-ext) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.3171
- Train Sparse Categorical Accuracy: 0.8870
- Validation Loss: 0.3344
- Validation Sparse Categorical Accuracy: 0.8768
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
| 0.4282     | 0.8574                            | 0.3700          | 0.8720                                 | 0     |
| 0.3583     | 0.8694                            | 0.3345          | 0.8672                                 | 1     |
| 0.3171     | 0.8870                            | 0.3344          | 0.8768                                 | 2     |


### Framework versions

- Transformers 4.16.0
- TensorFlow 2.7.0
- Datasets 1.18.1
- Tokenizers 0.11.0
