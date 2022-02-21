---
license: apache-2.0
tags:
- generated_from_keras_callback
model-index:
- name: nickmuchi/nickmuchi-finetuned-summa-amazon-en-es
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# nickmuchi/nickmuchi-finetuned-summa-amazon-en-es

This model is a fine-tuned version of [google/mt5-small](https://huggingface.co/google/mt5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 4.0583
- Validation Loss: 3.3448
- Epoch: 7

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: {'name': 'AdamWeightDecay', 'learning_rate': {'class_name': 'PolynomialDecay', 'config': {'initial_learning_rate': 5.6e-05, 'decay_steps': 9672, 'end_learning_rate': 0.0, 'power': 1.0, 'cycle': False, 'name': None}}, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-08, 'amsgrad': False, 'weight_decay_rate': 0.01}
- training_precision: mixed_float16

### Training results

| Train Loss | Validation Loss | Epoch |
|:----------:|:---------------:|:-----:|
| 9.9283     | 4.5300          | 0     |
| 5.9451     | 3.7821          | 1     |
| 5.1507     | 3.5895          | 2     |
| 4.7195     | 3.4841          | 3     |
| 4.4421     | 3.4231          | 4     |
| 4.2489     | 3.3754          | 5     |
| 4.1194     | 3.3519          | 6     |
| 4.0583     | 3.3448          | 7     |


### Framework versions

- Transformers 4.15.0
- TensorFlow 2.7.0
- Datasets 1.17.0
- Tokenizers 0.10.3
