---
tags:
- generated_from_trainer
datasets:
- squad
model-index:
- name: bert-base-turkish-128k-cased-finetuned_lr-2e-05_epochs-3TQUAD2-finetuned_lr-2e-05_epochs-1
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-turkish-128k-cased-finetuned_lr-2e-05_epochs-3TQUAD2-finetuned_lr-2e-05_epochs-1

This model is a fine-tuned version of [husnu/bert-base-turkish-128k-cased-finetuned_lr-2e-05_epochs-3](https://huggingface.co/husnu/bert-base-turkish-128k-cased-finetuned_lr-2e-05_epochs-3) on the squad dataset.
It achieves the following results on the evaluation set:
- Loss: 1.4196

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
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 1

### Training results

| Training Loss | Epoch | Step | Validation Loss |
|:-------------:|:-----:|:----:|:---------------:|
| 0.5885        | 1.0   | 2245 | 1.4196          |


### Framework versions

- Transformers 4.15.0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
