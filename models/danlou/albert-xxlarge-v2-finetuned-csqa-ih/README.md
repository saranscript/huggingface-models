---
license: apache-2.0
tags:
- generated_from_trainer
metrics:
- accuracy
model_index:
  name: albert-xxlarge-v2-finetuned-csqa-ih
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-xxlarge-v2-finetuned-csqa-ih

This model is a fine-tuned version of [albert-xxlarge-v2](https://huggingface.co/albert-xxlarge-v2) on an unkown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.5694
- Accuracy: 0.8026

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 1e-05
- train_batch_size: 16
- eval_batch_size: 16
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 0.8032        | 1.0   | 532  | 0.5217          | 0.8043   |
| 0.3182        | 2.0   | 1064 | 0.6313          | 0.7985   |
| 0.0668        | 3.0   | 1596 | 1.2971          | 0.7969   |
| 0.0131        | 4.0   | 2128 | 1.4671          | 0.8026   |
| 0.0046        | 5.0   | 2660 | 1.5694          | 0.8026   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0
- Datasets 1.10.2
- Tokenizers 0.10.3
