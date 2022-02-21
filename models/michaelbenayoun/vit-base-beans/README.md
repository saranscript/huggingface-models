---
license: apache-2.0
tags:
- image-classification
- generated_from_trainer
datasets:
- cifar10
metrics:
- accuracy
model-index:
- name: vit-base-beans
  results:
  - task:
      name: Image Classification
      type: image-classification
    dataset:
      name: cifar10
      type: cifar10
      args: plain_text
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.6224
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# vit-base-beans

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on the cifar10 dataset.
It achieves the following results on the evaluation set:
- Loss: 2.1333
- Accuracy: 0.6224

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
- seed: 1337
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- training_steps: 100

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 2.1678        | 0.02  | 100  | 2.1333          | 0.6224   |


### Framework versions

- Transformers 4.15.0.dev0
- Pytorch 1.10.0
- Datasets 1.16.2.dev0
- Tokenizers 0.10.2
