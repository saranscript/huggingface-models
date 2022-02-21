---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- clinc_oos
metrics:
- accuracy
model-index:
- name: distilbert-base-uncased-distilled-clinc
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: clinc_oos
      type: clinc_oos
      args: plus
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.9467741935483871
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# distilbert-base-uncased-distilled-clinc

This model is a fine-tuned version of [distilbert-base-uncased](https://huggingface.co/distilbert-base-uncased) on the clinc_oos dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2795
- Accuracy: 0.9468

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
- train_batch_size: 48
- eval_batch_size: 48
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| 3.4223        | 1.0   | 318  | 2.5556          | 0.7561   |
| 1.9655        | 2.0   | 636  | 1.3075          | 0.8577   |
| 1.0041        | 3.0   | 954  | 0.6970          | 0.9165   |
| 0.5449        | 4.0   | 1272 | 0.4637          | 0.9339   |
| 0.3424        | 5.0   | 1590 | 0.3630          | 0.9397   |
| 0.247         | 6.0   | 1908 | 0.3225          | 0.9442   |
| 0.1968        | 7.0   | 2226 | 0.2983          | 0.9458   |
| 0.1693        | 8.0   | 2544 | 0.2866          | 0.9465   |
| 0.1547        | 9.0   | 2862 | 0.2820          | 0.9468   |
| 0.1477        | 10.0  | 3180 | 0.2795          | 0.9468   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.10.0+cu111
- Datasets 1.16.1
- Tokenizers 0.10.3
