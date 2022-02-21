---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- matthews_correlation
model-index:
- name: distilbert-base-uncased-cola
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
      value: 0.5301312348234369
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-cola

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2715
- Matthews Correlation: 0.5301

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
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Matthews Correlation |
|:-------------:|:-----:|:----:|:---------------:|:--------------------:|
| 0.5216        | 1.0   | 535  | 0.5124          | 0.4104               |
| 0.3456        | 2.0   | 1070 | 0.5700          | 0.4692               |
| 0.2362        | 3.0   | 1605 | 0.7277          | 0.4844               |
| 0.1818        | 4.0   | 2140 | 0.7553          | 0.5007               |
| 0.1509        | 5.0   | 2675 | 0.9406          | 0.4987               |
| 0.1017        | 6.0   | 3210 | 0.9475          | 0.5387               |
| 0.0854        | 7.0   | 3745 | 1.0933          | 0.5317               |
| 0.051         | 8.0   | 4280 | 1.1719          | 0.5358               |
| 0.0512        | 9.0   | 4815 | 1.2296          | 0.5321               |
| 0.0308        | 10.0  | 5350 | 1.2715          | 0.5301               |


### Framework versions

- Transformers 4.12.3
- Pytorch 1.10.0+cu102
- Datasets 1.15.1
- Tokenizers 0.10.3
