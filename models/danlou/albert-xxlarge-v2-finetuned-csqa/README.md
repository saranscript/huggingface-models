---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- commonsense_qa
metrics:
- accuracy
model_index:
- name: albert-xxlarge-v2-finetuned-csqa
  results:
  - dataset:
      name: commonsense_qa
      type: commonsense_qa
      args: default
    metric:
      name: Accuracy
      type: accuracy
      value: 0.7870597839355469
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# albert-xxlarge-v2-finetuned-csqa

This model is a fine-tuned version of [albert-xxlarge-v2](https://huggingface.co/albert-xxlarge-v2) on the commonsense_qa dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6177
- Accuracy: 0.7871

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
| 0.7464        | 1.0   | 609  | 0.5319          | 0.7985   |
| 0.3116        | 2.0   | 1218 | 0.6422          | 0.7936   |
| 0.0769        | 3.0   | 1827 | 1.2674          | 0.7952   |
| 0.0163        | 4.0   | 2436 | 1.4839          | 0.7903   |
| 0.0122        | 5.0   | 3045 | 1.6177          | 0.7871   |


### Framework versions

- Transformers 4.8.2
- Pytorch 1.9.0
- Datasets 1.10.2
- Tokenizers 0.10.3
