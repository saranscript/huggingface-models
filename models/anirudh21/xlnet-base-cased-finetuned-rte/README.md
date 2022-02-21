---
license: mit
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: xlnet-base-cased-finetuned-rte
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
      value: 0.6895306859205776
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlnet-base-cased-finetuned-rte

This model is a fine-tuned version of [xlnet-base-cased](https://huggingface.co/xlnet-base-cased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.0656
- Accuracy: 0.6895

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
| No log        | 1.0   | 156  | 0.7007          | 0.4874   |
| No log        | 2.0   | 312  | 0.6289          | 0.6751   |
| No log        | 3.0   | 468  | 0.7020          | 0.6606   |
| 0.6146        | 4.0   | 624  | 1.0573          | 0.6570   |
| 0.6146        | 5.0   | 780  | 1.0656          | 0.6895   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
