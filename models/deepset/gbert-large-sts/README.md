---
language: de
license: mit
tags:
- exbert
---

## Overview
**Language model:** gbert-large-sts

**Language:** German  
**Training data:** German STS benchmark train and dev set  
**Eval data:** German STS benchmark test set   
**Infrastructure**: 1x V100 GPU  
**Published**: August 12th, 2021

## Details
- We trained a gbert-large model on the task of estimating semantic similarity of German-language text pairs. The dataset is a machine-translated version of the [STS benchmark](https://ixa2.si.ehu.eus/stswiki/index.php/STSbenchmark), which is available [here](https://github.com/t-systems-on-site-services-gmbh/german-STSbenchmark).

## Hyperparameters
```
batch_size = 16
n_epochs = 4
warmup_ratio = 0.1
learning_rate = 2e-5
lr_schedule = LinearWarmup
```
## Performance
Stay tuned... and watch out for new papers on arxiv.org ;)

## Authors
- Julian Risch: `julian.risch [at] deepset.ai`
- Timo Möller: `timo.moeller [at] deepset.ai`
- Julian Gutsch: `julian.gutsch [at] deepset.ai`
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
[Twitter](https://twitter.com/deepset_ai) | [LinkedIn](https://www.linkedin.com/company/deepset-ai/) | [Website](https://deepset.ai)  

By the way: [we're hiring!](http://www.deepset.ai/jobs)
