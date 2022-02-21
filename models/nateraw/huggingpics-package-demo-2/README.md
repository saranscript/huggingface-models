---
license: apache-2.0
tags:
- image-classification
- huggingpics
- generated_from_trainer

---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# huggingpics-package-demo-2

This model is a fine-tuned version of [google/vit-base-patch16-224-in21k](https://huggingface.co/google/vit-base-patch16-224-in21k) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.3761
- Acc: 0.9403

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
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4.0
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Acc    |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 1.0328        | 1.0   | 24   | 0.9442          | 0.7463 |
| 0.8742        | 2.0   | 48   | 0.7099          | 0.9403 |
| 0.6451        | 3.0   | 72   | 0.5050          | 0.9403 |
| 0.508         | 4.0   | 96   | 0.3761          | 0.9403 |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.9.0+cu111
- Tokenizers 0.10.3
