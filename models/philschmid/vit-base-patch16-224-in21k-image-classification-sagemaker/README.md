---
tags:
- image-classification
metrics:
- accuracy

model-index:
- name: vit-base-patch16-224-in21k-image-classification-sagemaker
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# vit-base-patch16-224-in21k-image-classification-sagemaker

This model is a fine-tuned version of [vit-base-patch16-224-in21k](https://huggingface.co/vit-base-patch16-224-in21k) on the cifar10 dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3033
- Accuracy: 0.972

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
- train_batch_size: 16
- eval_batch_size: 64
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 500
- num_epochs: 3

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 313  | 1.4603          | 0.936    |
| 1.6548        | 2.0   | 626  | 0.4451          | 0.966    |
| 1.6548        | 3.0   | 939  | 0.3033          | 0.972    |


### Framework versions

- Transformers 4.6.1
- Pytorch 1.7.1
- Datasets 1.6.2
- Tokenizers 0.10.3
