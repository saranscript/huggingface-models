---
language: en
datasets:
- squad_v2
license: mit
thumbnail: https://thumb.tildacdn.com/tild3433-3637-4830-a533-353833613061/-/resize/720x/-/format/webp/germanquad.jpg
tags:
- exbert
---

## Overview
**Language model:** deepset/tinybert-6L-768D-squad2   
**Language:** English  
**Training data:** SQuAD 2.0 training set x 20 augmented + SQuAD 2.0 training set without augmentation
**Eval data:** SQuAD 2.0 dev set
**Infrastructure**: 1x V100 GPU  
**Published**: Dec 8th, 2021

## Details
- haystack's intermediate layer and prediction layer distillation features were used for training (based on [TinyBERT](https://arxiv.org/pdf/1909.10351.pdf)). deepset/bert-base-uncased-squad2 was used as the teacher model and huawei-noah/TinyBERT_General_6L_768D was used as the student model.

## Hyperparameters
### Intermediate layer distillation
```
batch_size = 26
n_epochs = 5
max_seq_len = 384
learning_rate = 5e-5
lr_schedule = LinearWarmup
embeds_dropout_prob = 0.1
temperature = 1
```
### Prediction layer distillation 
```
batch_size = 26
n_epochs = 5
max_seq_len = 384
learning_rate = 3e-5
lr_schedule = LinearWarmup
embeds_dropout_prob = 0.1
temperature = 1
distillation_loss_weight = 1.0
```
## Performance
```
"exact": 71.87736882001179
"f1": 76.36111895973675
```

## Authors
- Timo Möller: `timo.moeller [at] deepset.ai`
- Julian Risch: `julian.risch [at] deepset.ai`
- Malte Pietsch: `malte.pietsch [at] deepset.ai`
- Michel Bartels: `michel.bartels [at] deepset.ai`
## About us
![deepset logo](https://workablehr.s3.amazonaws.com/uploads/account/logo/476306/logo)
We bring NLP to the industry via open source!  
Our focus: Industry specific language models & large scale QA systems.  
  
Some of our work: 
- [German BERT (aka "bert-base-german-cased")](https://deepset.ai/german-bert)
- [GermanQuAD and GermanDPR datasets and models (aka "gelectra-base-germanquad", "gbert-base-germandpr")](https://deepset.ai/germanquad)
- [FARM](https://github.com/deepset-ai/FARM)
- [Haystack](https://github.com/deepset-ai/haystack/)

Get in touch:
[Twitter](https://twitter.com/deepset_ai) | [LinkedIn](https://www.linkedin.com/company/deepset-ai/) | [Slack](https://haystack.deepset.ai/community/join) | [GitHub Discussions](https://github.com/deepset-ai/haystack/discussions) | [Website](https://deepset.ai)

By the way: [we're hiring!](http://www.deepset.ai/jobs)