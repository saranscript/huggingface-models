---
license: mit
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- accuracy
model-index:
- name: xlnet-base-cased-finetuned-wnli
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: wnli
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.5633802816901409
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# xlnet-base-cased-finetuned-wnli

This model is a fine-tuned version of [xlnet-base-cased](https://huggingface.co/xlnet-base-cased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.6874
- Accuracy: 0.5634

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
| No log        | 1.0   | 40   | 0.7209          | 0.5352   |
| No log        | 2.0   | 80   | 0.6874          | 0.5634   |
| No log        | 3.0   | 120  | 0.6908          | 0.5634   |
| No log        | 4.0   | 160  | 0.6987          | 0.4930   |
| No log        | 5.0   | 200  | 0.6952          | 0.5634   |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
