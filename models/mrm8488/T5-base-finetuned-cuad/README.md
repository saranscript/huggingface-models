---
language:
- en
license: mit
tags:
- generated_from_trainer
datasets:
- cuad
model-index:
- name: T5-base-cuad-512
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# T5-base fine-tuned on CUAD for Legal Contract Review (via QA)

This model is a fine-tuned version of [t5-base](https://huggingface.co/t5-base) on the cuad dataset.
It achieves the following results on the evaluation set:
- Loss: 0.2209

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
- train_batch_size: 4
- eval_batch_size: 4
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 10

### Training results

| Training Loss | Epoch | Step  | Validation Loss |
|:-------------:|:-----:|:-----:|:---------------:|
| 0.2809        | 1.0   | 2795  | 0.2331          |
| 0.2459        | 2.0   | 5590  | 0.2253          |
| 0.2355        | 3.0   | 8385  | 0.2220          |
| 0.2212        | 4.0   | 11180 | 0.2203          |
| 0.2068        | 5.0   | 13975 | 0.2197          |
| 0.2085        | 6.0   | 16770 | 0.2194          |
| 0.1968        | 7.0   | 19565 | 0.2199          |
| 0.1906        | 8.0   | 22360 | 0.2200          |
| 0.1909        | 9.0   | 25155 | 0.2208          |
| 0.1788        | 10.0  | 27950 | 0.2209          |


### Framework versions

- Transformers 4.16.0.dev0
- Pytorch 1.10.0+cu111
- Datasets 1.17.0
- Tokenizers 0.10.3
