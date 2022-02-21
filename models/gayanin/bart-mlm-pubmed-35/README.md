---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-mlm-pubmed-35
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-mlm-pubmed-35

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 0.9359
- Rouge2 Precision: 0.5451
- Rouge2 Recall: 0.4232
- Rouge2 Fmeasure: 0.4666

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
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge2 Precision | Rouge2 Recall | Rouge2 Fmeasure |
|:-------------:|:-----:|:----:|:---------------:|:----------------:|:-------------:|:---------------:|
| 1.4156        | 1.0   | 663  | 1.0366          | 0.5165           | 0.3967        | 0.4394          |
| 1.1773        | 2.0   | 1326 | 0.9841          | 0.5354           | 0.4168        | 0.4589          |
| 1.0894        | 3.0   | 1989 | 0.9554          | 0.5346           | 0.4133        | 0.4563          |
| 0.9359        | 4.0   | 2652 | 0.9440          | 0.5357           | 0.4163        | 0.4587          |
| 0.8758        | 5.0   | 3315 | 0.9340          | 0.5428           | 0.4226        | 0.465           |
| 0.8549        | 6.0   | 3978 | 0.9337          | 0.5385           | 0.422         | 0.4634          |
| 0.7743        | 7.0   | 4641 | 0.9330          | 0.542            | 0.422         | 0.4647          |
| 0.7465        | 8.0   | 5304 | 0.9315          | 0.5428           | 0.4231        | 0.4654          |
| 0.7348        | 9.0   | 5967 | 0.9344          | 0.5462           | 0.4244        | 0.4674          |
| 0.7062        | 10.0  | 6630 | 0.9359          | 0.5451           | 0.4232        | 0.4666          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
