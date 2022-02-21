---
license: apache-2.0
tags:
- generated_from_trainer
model-index:
- name: t5-small-mlm-pubmed-45
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-mlm-pubmed-45

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.6395
- Rouge2 Precision: 0.3383
- Rouge2 Recall: 0.2424
- Rouge2 Fmeasure: 0.2753

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
| 2.519         | 0.75  | 500  | 1.9659          | 0.3178           | 0.1888        | 0.2299          |
| 2.169         | 1.51  | 1000 | 1.8450          | 0.3256           | 0.2138        | 0.25            |
| 2.0796        | 2.26  | 1500 | 1.7900          | 0.3368           | 0.2265        | 0.2636          |
| 1.9978        | 3.02  | 2000 | 1.7553          | 0.3427           | 0.234         | 0.2709          |
| 1.9686        | 3.77  | 2500 | 1.7172          | 0.3356           | 0.2347        | 0.2692          |
| 1.9142        | 4.52  | 3000 | 1.6986          | 0.3358           | 0.238         | 0.2715          |
| 1.921         | 5.28  | 3500 | 1.6770          | 0.3349           | 0.2379        | 0.2709          |
| 1.8848        | 6.03  | 4000 | 1.6683          | 0.3346           | 0.2379        | 0.2708          |
| 1.8674        | 6.79  | 4500 | 1.6606          | 0.3388           | 0.2419        | 0.2752          |
| 1.8606        | 7.54  | 5000 | 1.6514          | 0.3379           | 0.2409        | 0.274           |
| 1.8515        | 8.3   | 5500 | 1.6438          | 0.3356           | 0.2407        | 0.2731          |
| 1.8403        | 9.05  | 6000 | 1.6401          | 0.3367           | 0.2421        | 0.2744          |
| 1.8411        | 9.8   | 6500 | 1.6395          | 0.3383           | 0.2424        | 0.2753          |


### Framework versions

- Transformers 4.12.5
- Pytorch 1.10.0+cu111
- Datasets 1.15.1
- Tokenizers 0.10.3
