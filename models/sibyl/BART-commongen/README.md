---
tags:
- generated_from_trainer
datasets:
- gem
model_index:
- name: BART-commongen
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

# BART-commongen

This model is a fine-tuned version of [facebook/bart-base](https://huggingface.co/facebook/bart-base) on the gem dataset.
It achieves the following results on the evaluation set:
- Loss: 1.1263
- Spice: 0.4178

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
| 9.0971        | 0.05  | 100  | 4.1336          | 0.3218 |
| 3.5348        | 0.09  | 200  | 1.5467          | 0.3678 |
| 1.5099        | 0.14  | 300  | 1.1280          | 0.3821 |
| 1.2395        | 0.19  | 400  | 1.1178          | 0.3917 |
| 1.1827        | 0.24  | 500  | 1.0919          | 0.4086 |
| 1.1545        | 0.28  | 600  | 1.1028          | 0.4035 |
| 1.1363        | 0.33  | 700  | 1.1021          | 0.4187 |
| 1.1156        | 0.38  | 800  | 1.1231          | 0.4103 |
| 1.1077        | 0.43  | 900  | 1.1221          | 0.4117 |
| 1.0964        | 0.47  | 1000 | 1.1169          | 0.4088 |
| 1.0704        | 0.52  | 1100 | 1.1143          | 0.4133 |
| 1.0483        | 0.57  | 1200 | 1.1085          | 0.4058 |
| 1.0556        | 0.62  | 1300 | 1.1059          | 0.4249 |
| 1.0343        | 0.66  | 1400 | 1.0992          | 0.4102 |
| 1.0123        | 0.71  | 1500 | 1.1126          | 0.4104 |
| 1.0108        | 0.76  | 1600 | 1.1140          | 0.4177 |
| 1.005         | 0.81  | 1700 | 1.1264          | 0.4078 |
| 0.9822        | 0.85  | 1800 | 1.1256          | 0.4158 |
| 0.9918        | 0.9   | 1900 | 1.1345          | 0.4118 |
| 0.9664        | 0.95  | 2000 | 1.1087          | 0.4073 |
| 0.9532        | 1.0   | 2100 | 1.1217          | 0.4063 |
| 0.8799        | 1.04  | 2200 | 1.1229          | 0.4115 |
| 0.8665        | 1.09  | 2300 | 1.1263          | 0.4178 |


### Framework versions

- Transformers 4.9.2
- Pytorch 1.9.0+cu102
- Datasets 1.11.1.dev0
- Tokenizers 0.10.3
