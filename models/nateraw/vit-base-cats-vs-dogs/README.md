---
license: apache-2.0
tags:
- generated_from_trainer
- image-classification
- pytorch
datasets:
- cats_vs_dogs
metrics:
- accuracy
model-index:
- name: vit-base-cats-vs-dogs
  results:
  - task:
      name: Image Classification
      type: image-classification
    dataset:
      name: cats_vs_dogs
      type: cats_vs_dogs
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9934510250569476
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# vit-base-cats-vs-dogs

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on the cats_vs_dogs dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0202
- Accuracy: 0.9935

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0002
- train_batch_size: 64
- eval_batch_size: 64
- seed: 1337
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.064         | 1.0   | 311  | 0.0483          | 0.9849   |
| 0.0622        | 2.0   | 622  | 0.0275          | 0.9903   |
| 0.0366        | 3.0   | 933  | 0.0262          | 0.9917   |
| 0.0294        | 4.0   | 1244 | 0.0219          | 0.9932   |
| 0.0161        | 5.0   | 1555 | 0.0202          | 0.9935   |


### Framework versions

- Transformers 4.8.1
- Pytorch 1.9.0+cu102
- Datasets 1.11.1.dev0
- Tokenizers 0.10.3
