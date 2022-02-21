---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: bart-mlm-pubmed-45
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# bart-mlm-pubmed-45

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1797
- Rouge2 Precision: 0.4333
- Rouge2 Recall: 0.3331
- Rouge2 Fmeasure: 0.3684

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
| 1.7989        | 1.0   | 663  | 1.3385          | 0.4097           | 0.3086        | 0.3444          |
| 1.5072        | 2.0   | 1326 | 1.2582          | 0.4218           | 0.3213        | 0.3569          |
| 1.4023        | 3.0   | 1989 | 1.2236          | 0.4207           | 0.3211        | 0.3562          |
| 1.2205        | 4.0   | 2652 | 1.2025          | 0.4359           | 0.3331        | 0.3696          |
| 1.1584        | 5.0   | 3315 | 1.1910          | 0.4304           | 0.3307        | 0.3658          |
| 1.1239        | 6.0   | 3978 | 1.1830          | 0.4247           | 0.3279        | 0.3618          |
| 1.0384        | 7.0   | 4641 | 1.1761          | 0.4308           | 0.3325        | 0.367           |
| 1.0168        | 8.0   | 5304 | 1.1762          | 0.4314           | 0.3336        | 0.368           |
| 0.9966        | 9.0   | 5967 | 1.1773          | 0.4335           | 0.3341        | 0.369           |
| 0.961         | 10.0  | 6630 | 1.1797          | 0.4333           | 0.3331        | 0.3684          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
