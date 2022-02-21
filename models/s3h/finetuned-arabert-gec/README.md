---
tags:
- generated_from_keras_callback
model-index:
- name: s3h/finetuned-arabert-gec
  results: []
---

<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# s3h/finetuned-arabert-gec

This model is a fine-tuned version of [aubmindlab/bert-base-arabertv02](https://huggingface.co/aubmindlab/bert-base-arabertv02) on an unknown dataset.
It achieves the following results on the evaluation set:
- Train Loss: -0.1214
- Train Pooler Output Loss: -0.1214
- Validation Loss: -0.1303
- Validation Pooler Output Loss: -0.1303
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
- optimizer: {'name': 'AdamWeightDecay', 'learning_rate': {'class_name': 'PolynomialDecay', 'config': {'initial_learning_rate': 5e-05, 'decay_steps': 3, 'end_learning_rate': 0.0, 'power': 1.0, 'cycle': False, 'name': None}}, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-08, 'amsgrad': False, 'weight_decay_rate': 0.01}
- training_precision: mixed_float16

### Training results

| Train Loss | Train Pooler Output Loss | Validation Loss | Validation Pooler Output Loss | Epoch |
|:----------:|:------------------------:|:---------------:|:-----------------------------:|:-----:|
| -0.0492    | -0.0492                  | -0.0918         | -0.0918                       | 0     |
| -0.0949    | -0.0949                  | -0.1146         | -0.1146                       | 1     |
| -0.1214    | -0.1214                  | -0.1303         | -0.1303                       | 2     |


### Framework versions

- Transformers 4.14.1
- TensorFlow 2.6.2
- Datasets 1.17.0
- Tokenizers 0.10.3
