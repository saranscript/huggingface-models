---
license: apache-2.0
tags:
- image-classification
- generated_from_trainer
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
      value: 0.9937357630979499
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# vit-base-cats-vs-dogs

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on the cats_vs_dogs dataset.
It achieves the following results on the evaluation set:
- Loss: 0.0182
- Accuracy: 0.9937

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
- train_batch_size: 32
- eval_batch_size: 32
- seed: 1337
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.1177        | 1.0   | 622  | 0.0473          | 0.9832   |
| 0.057         | 2.0   | 1244 | 0.0362          | 0.9883   |
| 0.0449        | 3.0   | 1866 | 0.0261          | 0.9886   |
| 0.066         | 4.0   | 2488 | 0.0248          | 0.9923   |
| 0.0328        | 5.0   | 3110 | 0.0182          | 0.9937   |


### Framework versions

- Transformers 4.13.0.dev0
- Pytorch 1.8.1+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
