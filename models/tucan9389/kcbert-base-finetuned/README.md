---
tags:
- generated_from_trainer
datasets:
- klue
metrics:
- accuracy
model-index:
- name: kcbert-base-finetuned
  results:
  - task:
      name: Text Classification
      type: text-classification
    dataset:
      name: klue
      type: klue
      args: ynat
    metrics:
    - name: Accuracy
      type: accuracy
      value: 0.8329856154606347
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# kcbert-base-finetuned

This model is a fine-tuned version of [beomi/kcbert-base](https://huggingface.co/beomi/kcbert-base) on the klue dataset.
It achieves the following results on the evaluation set:
- Loss: 0.7393
- Accuracy: 0.8330

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

| Training Loss | Epoch | Step  | Validation Loss | Accuracy |
|:-------------:|:-----:|:-----:|:---------------:|:--------:|
| 0.4612        | 1.0   | 2855  | 0.5216          | 0.8143   |
| 0.3061        | 2.0   | 5710  | 0.5130          | 0.8248   |
| 0.2129        | 3.0   | 8565  | 0.6062          | 0.8257   |
| 0.1337        | 4.0   | 11420 | 0.7393          | 0.8330   |
| 0.0653        | 5.0   | 14275 | 0.8651          | 0.8302   |


### Framework versions

- Transformers 4.11.3
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
