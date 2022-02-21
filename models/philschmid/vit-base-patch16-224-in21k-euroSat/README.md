---
license: apache-2.0
tags:
- generated_from_keras_callback
widget:
- src: https://cdn.prod.www.spiegel.de/images/6b1135cd-0001-0004-0000-000000867699_w996_r1.778_fpx50_fpy47.38.jpg
metrics:
- accuracy
model-index:
- name: philschmid/vit-base-patch16-224-in21k-euroSat
  results:
  - task:
      name: Image Classification
      type: image-classification
    dataset:
      name: eurosat
      type: eurosat
      args: default
    metrics:
    - name: accuracy
      type: accuracy
      value: 0.9906
    - name: top-3-accuracy
      type: top-3-accuracy
      value: 1.0000
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# philschmid/vit-base-patch16-224-in21k-euroSat

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.0218
- Train Accuracy: 0.9990
- Train Top-3-accuracy: 1.0000
- Validation Loss: 0.0440
- Validation Accuracy: 0.9906
- Validation Top-3-accuracy: 1.0
- Epoch: 5

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: {'inner_optimizer': {'class_name': 'AdamWeightDecay', 'config': {'name': 'AdamWeightDecay', 'learning_rate': {'class_name': 'PolynomialDecay', 'config': {'initial_learning_rate': 3e-05, 'decay_steps': 3585, 'end_learning_rate': 0.0, 'power': 1.0, 'cycle': False, 'name': None}}, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-08, 'amsgrad': False, 'weight_decay_rate': 0.01}}, 'dynamic': True, 'initial_scale': 32768.0, 'dynamic_growth_steps': 2000}
- training_precision: mixed_float16

### Training results

| Train Loss | Train Accuracy | Train Top-3-accuracy | Validation Loss | Validation Accuracy | Validation Top-3-accuracy | Epoch |
|:----------:|:--------------:|:--------------------:|:---------------:|:-------------------:|:-------------------------:|:-----:|
| 0.4692     | 0.9471         | 0.9878               | 0.1455          | 0.9861              | 0.9998                    | 1     |
| 0.0998     | 0.9888         | 0.9996               | 0.0821          | 0.9864              | 0.9995                    | 2     |
| 0.0517     | 0.9939         | 0.9999               | 0.0617          | 0.9871              | 1.0                       | 3     |
| 0.0309     | 0.9971         | 0.9999               | 0.0524          | 0.9878              | 0.9998                    | 4     |
| 0.0218     | 0.9990         | 1.0000               | 0.0440          | 0.9906              | 1.0                       | 5     |


### Framework versions

- Transformers 4.15.0
- TensorFlow 2.7.0
- Datasets 1.17.0
- Tokenizers 0.10.3
