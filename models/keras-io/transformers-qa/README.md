---
datasets:
- squad
license: apache-2.0
tags: 
- generated_from_keras_callback
metrics: 
- f1
model-index: 
- name: transformers-qa
  results: 
  - task: 
      name: "Question Answering"
      type: question-answering
    dataset: 
      type: squad
      name: SQuAD
      args: en
    metrics:
      []
widget: 
  - context: "Keras is an API designed for human beings, not machines. Keras follows best practices for reducing cognitive load: it offers consistent & simple APIs, it minimizes the number of user actions required for common use cases, and it provides clear and actionable feedback upon user error."
---
<!-- This model card has been generated automatically according to the information Keras had access to. You should
probably proofread and complete it, then remove this comment. -->

# Question Answering with Hugging Face Transformers and Keras 🤗❤️

This model is a fine-tuned version of [distilbert-base-cased](https://huggingface.co/distilbert-base-cased) on SQuAD dataset.
It achieves the following results on the evaluation set:
- Train Loss: 0.9300
- Validation Loss: 1.1437
- Epoch: 1

## Model description

Question answering model based on distilbert-base-cased, trained with 🤗Transformers + ❤️Keras.

## Intended uses & limitations

This model is trained for Question Answering tutorial for Keras.io.

## Training and evaluation data

It is trained on [SQuAD](https://huggingface.co/datasets/squad) question answering dataset. ⁉️ 

## Training procedure

Find the notebook in Keras Examples [here](https://keras.io/examples/nlp/question_answering/). ❤️

### Training hyperparameters

The following hyperparameters were used during training:
- optimizer: {'name': 'Adam', 'learning_rate': 5e-05, 'decay': 0.0, 'beta_1': 0.9, 'beta_2': 0.999, 'epsilon': 1e-07, 'amsgrad': False}
- training_precision: mixed_float16

### Training results

| Train Loss | Validation Loss | Epoch |
|:----------:|:---------------:|:-----:|
| 1.5145     | 1.1500          | 0     |
| 0.9300     | 1.1437          | 1     |
 

### Framework versions

- Transformers 4.16.0.dev0
- TensorFlow 2.6.0
- Datasets 1.16.2.dev0
- Tokenizers 0.10.3
