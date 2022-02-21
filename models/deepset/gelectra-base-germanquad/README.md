---
language: de
datasets:
- deepset/germanquad
license: mit
thumbnail: https://thumb.tildacdn.com/tild3433-3637-4830-a533-353833613061/-/resize/720x/-/format/webp/germanquad.jpg
tags:
- exbert
---

![bert_image](https://thumb.tildacdn.com/tild3433-3637-4830-a533-353833613061/-/resize/720x/-/format/webp/germanquad.jpg)

## Overview
**Language model:** gelectra-base-germanquad   
**Language:** German  
**Training data:** GermanQuAD train set (~ 12MB)  
**Eval data:** GermanQuAD test set (~ 5MB)   
**Infrastructure**: 1x V100 GPU  
**Published**: Apr 21st, 2021

## Details
- We trained a German question answering model with a gelectra-base model as its basis.
- The dataset is GermanQuAD, a new, German language dataset, which we hand-annotated and published [online](https://deepset.ai/germanquad).
- The training dataset is one-way annotated and contains 11518 questions and 11518 answers, while the test dataset is three-way annotated so that there are 2204 questions and with 2204·3−76 = 6536answers, because we removed 76 wrong answers.

See https://deepset.ai/germanquad for more details and dataset download in SQuAD format.

## Hyperparameters
```
batch_size = 24
n_epochs = 2
max_seq_len = 384
learning_rate = 3e-5
lr_schedule = LinearWarmup
embeds_dropout_prob = 0.1
```
## Performance
We evaluated the extractive question answering performance on our GermanQuAD test set.
Model types and training data are included in the model name. 
For finetuning XLM-Roberta, we use the English SQuAD v2.0 dataset.
The GELECTRA models are warm started on the German translation of SQuAD v1.1 and finetuned on \\\\germanquad. 
The human baseline was computed for the 3-way test set by taking one answer as prediction and the other two as ground truth.
![performancetable](https://lh3.google.com/u/0/d/1IFqkq8OZ7TFnGzxmW6eoxXSYa12f2M7O=w1970-h1546-iv1) 

## Authors
- Timo Möller: `timo.moeller [at] deepset.ai`
- Julian Risch: `julian.risch [at] deepset.ai`
- Malte Pietsch: `malte.pietsch [at] deepset.ai`
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
