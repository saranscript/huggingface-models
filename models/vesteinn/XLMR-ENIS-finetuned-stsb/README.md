---
license: agpl-3.0
pipeline_tag: sentence-similarity
tags:
- generated_from_trainer
datasets:
- glue
metrics:
- spearmanr
model-index:
- name: XLMR-ENIS-finetuned-stsb
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: glue
      type: glue
      args: stsb
    metrics:
    - name: Spearmanr
      type: spearmanr
      value: 0.8887885342806044
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# XLMR-ENIS-finetuned-stsb

This model is a fine-tuned version of [vesteinn/XLMR-ENIS](https://huggingface.co/vesteinn/XLMR-ENIS) on the glue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5232
- Pearson: 0.8915
- Spearmanr: 0.8888

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

| Training Loss | Epoch | Step | Validation Loss | Pearson | Spearmanr |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:---------:|
| No log        | 1.0   | 360  | 0.6330          | 0.8562  | 0.8570    |
| 1.2835        | 2.0   | 720  | 0.6368          | 0.8790  | 0.8781    |
| 0.4518        | 3.0   | 1080 | 0.5352          | 0.8883  | 0.8852    |
| 0.4518        | 4.0   | 1440 | 0.4881          | 0.8910  | 0.8885    |
| 0.288         | 5.0   | 1800 | 0.5232          | 0.8915  | 0.8888    |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.13.0
- Tokenizers 0.10.3
