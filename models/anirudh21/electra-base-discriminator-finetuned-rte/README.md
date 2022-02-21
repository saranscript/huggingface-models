---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: electra-base-discriminator-finetuned-rte
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: rte
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8231046931407943
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# electra-base-discriminator-finetuned-rte

This model is a fine-tuned version of [google/electra-base-discriminator](https://huggingface.co/google/electra-base-discriminator) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.4793
- Accuracy: 0.8231

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
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 156  | 0.6076          | 0.6570   |
| No log        | 2.0   | 312  | 0.4824          | 0.7762   |
| No log        | 3.0   | 468  | 0.4793          | 0.8231   |
| 0.4411        | 4.0   | 624  | 0.7056          | 0.7906   |
| 0.4411        | 5.0   | 780  | 0.6849          | 0.8159   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.18.0
- Tokenizers 0.10.3
