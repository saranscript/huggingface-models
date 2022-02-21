---
license: apache-2.0
tags:
- generated_from_trainer
datasets:
- null
model_index:
- name: bert-base-uncased-issues-128
  results:
  - task:
      name: Masked Language Modeling
      type: fill-mask
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bert-base-uncased-issues-128

This model is a fine-tuned version of [bert-base-uncased](https://huggingface.co/bert-base-uncased) on the None dataset.
It achieves the following results on the evaluation set:
- Loss: 1.2109

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 5e-05
- train_batch_size: 8
- eval_batch_size: 8
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 16

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 1.9845        | 1.0   | 1163  | 1.6403          |
| 1.5695        | 2.0   | 2326  | 1.4212          |
| 1.4221        | 3.0   | 3489  | 1.3714          |
| 1.3302        | 4.0   | 4652  | 1.3592          |
| 1.2734        | 5.0   | 5815  | 1.2781          |
| 1.2143        | 6.0   | 6978  | 1.2286          |
| 1.1704        | 7.0   | 8141  | 1.2492          |
| 1.1261        | 8.0   | 9304  | 1.2044          |
| 1.0812        | 9.0   | 10467 | 1.1878          |
| 1.0657        | 10.0  | 11630 | 1.2177          |
| 1.0319        | 11.0  | 12793 | 1.1428          |
| 1.0063        | 12.0  | 13956 | 1.0910          |
| 0.9731        | 13.0  | 15119 | 1.1111          |
| 0.9674        | 14.0  | 16282 | 1.1699          |
| 0.9391        | 15.0  | 17445 | 1.0805          |
| 0.9381        | 16.0  | 18608 | 1.2109          |


### Framework versions

- Transformers 4.8.0
- Pytorch 1.9.0+cu111
- Datasets 1.18.3
- Tokenizers 0.10.3
