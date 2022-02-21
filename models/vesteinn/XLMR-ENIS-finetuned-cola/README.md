---
license: agpl-3.0
tags:
- generated_from_trainer
datasets:
- glue
language: 
- en
- is
metrics:
- matthews_correlation
model-index:
- name: XLMR-ENIS-finetuned-cola
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
      value: 0.6306425398187112
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLMR-ENIS-finetuned-cola

This model is a fine-tuned version of [vesteinn/XLMR-ENIS](https://huggingface.co/vesteinn/XLMR-ENIS) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7311
- Matthews Correlation: 0.6306

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
| 0.5216        | 1.0   | 535  | 0.5836          | 0.4855               |
| 0.3518        | 2.0   | 1070 | 0.4426          | 0.5962               |
| 0.2538        | 3.0   | 1605 | 0.5091          | 0.6110               |
| 0.1895        | 4.0   | 2140 | 0.6955          | 0.6136               |
| 0.1653        | 5.0   | 2675 | 0.7311          | 0.6306               |


### Framework versions

- Transformers 4.10.3
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
