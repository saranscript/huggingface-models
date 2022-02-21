---
license: apache-2.0
tags:
- image-classification
- generated_from_trainer
datasets:
- beans
widget:
- src: https://huggingface.co/nateraw/vit-base-beans/resolve/main/healthy.jpeg
  example_title: Healthy
- src: https://huggingface.co/nateraw/vit-base-beans/resolve/main/angular_leaf_spot.jpeg
  example_title: Angular Leaf Spot
- src: https://huggingface.co/nateraw/vit-base-beans/resolve/main/bean_rust.jpeg
  example_title: Bean Rust
metrics:
- accuracy
model-index:
- name: vit-base-beans
  results:
  - task:
      name: Image Classification
      type: image-classification
    dataset:
      name: beans
      type: beans
      args: default
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9849624060150376
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# vit-base-beans

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on the beans dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0505
- Accuracy: 0.9850

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
- train_batch_size: 16
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 8
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.1166        | 1.54  | 100  | 0.0764          | 0.9850   |
| 0.1607        | 3.08  | 200  | 0.2114          | 0.9398   |
| 0.0067        | 4.62  | 300  | 0.0692          | 0.9774   |
| 0.005         | 6.15  | 400  | 0.0944          | 0.9624   |
| 0.0043        | 7.69  | 500  | 0.0505          | 0.9850   |


### Framework versions

- Transformers 4.16.2
- Pytorch 1.10.0+cu111
- Datasets 1.18.3
- Tokenizers 0.11.0
