---
tags:
- generated_from_trainer
datasets:
- klue
metrics:
- pearsonr
model_index:
- name: bert-base-finetuned-sts
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: klue
      type: klue
      args: sts
    metric:
      name: Pearsonr
      type: pearsonr
      value: 0.837527365741951
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-finetuned-sts

This model is a fine-tuned version of [klue/bert-base](https://huggingface.co/klue/bert-base) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.5657
- Pearsonr: 0.8375

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
- train_batch_size: 128
- eval_batch_size: 128
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 5

### Training results

| Training Loss | Epoch | Step | Validation Loss | Pearsonr |
|:-------------:|:-----:|:----:|:---------------:|:--------:|
| No log        | 1.0   | 92   | 0.8280          | 0.7680   |
| No log        | 2.0   | 184  | 0.6602          | 0.8185   |
| No log        | 3.0   | 276  | 0.5939          | 0.8291   |
| No log        | 4.0   | 368  | 0.5765          | 0.8367   |
| No log        | 5.0   | 460  | 0.5657          | 0.8375   |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.0
- Tokenizers 0.10.3
