---
license: mit
tags:
- generated_from_trainer
datasets:
- gem
model_index:
- name: BART-large-commongen
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: gem
      type: gem
      args: common_gen
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# BART-large-commongen

This model is a fine-tuned version of [facebook/bart-large](https://huggingface.co/facebook/bart-large) on the gem dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1409
- Spice: 0.4009

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 0.0001
- train_batch_size: 32
- eval_batch_size: 32
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- lr_scheduler_warmup_steps: 1000
- training_steps: 6317

### Training results

| Training Loss | Epoch | Step | Validation Loss | Spice  |
|:-------------:|:-----:|:----:|:---------------:|:------:|
| 10.1086       | 0.05  | 100  | 4.9804          | 0.3736 |
| 4.4168        | 0.09  | 200  | 2.4402          | 0.4079 |
| 1.8158        | 0.14  | 300  | 1.1096          | 0.4258 |
| 1.1723        | 0.19  | 400  | 1.0845          | 0.4086 |
| 1.0894        | 0.24  | 500  | 1.0727          | 0.423  |
| 1.0949        | 0.28  | 600  | 1.0889          | 0.4224 |
| 1.0773        | 0.33  | 700  | 1.0977          | 0.4201 |
| 1.0708        | 0.38  | 800  | 1.1157          | 0.4213 |
| 1.0663        | 0.43  | 900  | 1.1798          | 0.421  |
| 1.0985        | 0.47  | 1000 | 1.1611          | 0.4025 |
| 1.0561        | 0.52  | 1100 | 1.1048          | 0.421  |
| 1.0594        | 0.57  | 1200 | 1.2044          | 0.3626 |
| 1.0689        | 0.62  | 1300 | 1.1409          | 0.4009 |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.1.dev0
- Tokenizers 0.10.3
