---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- matthews_correlation
model-index:
- name: distilbert-base-uncased-finetuned-cola
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: cola
    metrics:
    - name: Matthews Correlation
      type: matthews_correlation
      value: 0.509687043672971
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-finetuned-cola

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7512
- Matthews Correlation: 0.5097

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

| Training Loss | Epoch | Step | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:----:|:---------------:|:--------------------:|
| 0.5237        | 1.0   | 535  | 0.5117          | 0.4469               |
| 0.3496        | 2.0   | 1070 | 0.5538          | 0.4965               |
| 0.2377        | 3.0   | 1605 | 0.6350          | 0.4963               |
| 0.1767        | 4.0   | 2140 | 0.7512          | 0.5097               |
| 0.1383        | 5.0   | 2675 | 0.8647          | 0.5056               |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.8.1+cu102
- Datasets 1.15.1
- Tokenizers 0.10.1
