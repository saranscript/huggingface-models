---
language: de
datasets:
- deepset/germandpr
license: mit
thumbnail: https://thumb.tildacdn.com/tild3433-3637-4830-a533-353833613061/-/resize/720x/-/format/webp/germanquad.jpg
tags:
- exbert
---

![bert_image](https://thumb.tildacdn.com/tild3433-3637-4830-a533-353833613061/-/resize/720x/-/format/webp/germanquad.jpg)

## Overview
**Language model:** gbert-base-germandpr   
**Language:** German  
**Training data:** GermanDPR train set (~ 56MB)  
**Eval data:** GermanDPR test set (~ 6MB)   
**Infrastructure**: 4x V100 GPU  
**Published**: Apr 26th, 2021

## Details
- We trained a dense passage retrieval model with two gbert-base models as encoders of questions and passages.
- The dataset is GermanDPR, a new, German language dataset, which we hand-annotated and published [online](https://deepset.ai/germanquad).
- It comprises 9275 question/answer pairs in the training set and 1025 pairs in the test set.
For each pair, there are one positive context and three hard negative contexts.
- As the basis of the training data, we used our hand-annotated GermanQuAD dataset as positive samples and generated hard negative samples from the latest German Wikipedia dump (6GB of raw txt files).
- The data dump was cleaned with tailored scripts, leading to 2.8 million indexed passages from German Wikipedia.

See https://deepset.ai/germanquad for more details and dataset download.

## Hyperparameters
```
batch_size = 40
n_epochs = 20
num_training_steps = 4640
num_warmup_steps = 460
max_seq_len = 32 tokens for question encoder and 300 tokens for passage encoder
learning_rate = 1e-6
lr_schedule = LinearWarmup
embeds_dropout_prob = 0.1
num_hard_negatives = 2
```
## Performance
During training, we monitored the in-batch average rank and the loss and evaluated different batch sizes, numbers of epochs, and number of hard negatives on a dev set split from the train set.
The dev split contained 1030 question/answer pairs.
Even without thorough hyperparameter tuning, we observed quite stable learning. Multiple restarts with different seeds produced quite similar results.
Note that the in-batch average rank is influenced by settings for batch size and number of hard negatives. A smaller number of hard negatives makes the task easier.
After fixing the hyperparameters we trained the model on the full GermanDPR train set.
  
We further evaluated the retrieval performance of the trained model on the full German Wikipedia with the GermanDPR test set as labels. To this end, we converted the GermanDPR test set to SQuAD format. The DPR model drastically outperforms the BM25 baseline with regard to recall@k.
![performancetable](https://lh3.google.com/u/0/d/1lX6G0cp4NTx1yUWs74LI0Gcs41sYy_Fb=w2880-h1578-iv1)

## Usage
### In haystack
You can load the model in [haystack](https://github.com/deepset-ai/haystack/) as a retriever for doing QA at scale:
```python
retriever = DensePassageRetriever(
  document_store=document_store,
  query_embedding_model="deepset/gbert-base-germandpr-question_encoder"
  passage_embedding_model="deepset/gbert-base-germandpr-ctx_encoder"
)
```

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
[Twitter](https://twitter.com/deepset_ai) | [LinkedIn](https://www.linkedin.com/company/deepset-ai/) | [Website](https://deepset.ai)  

By the way: [we're hiring!](http://www.deepset.ai/jobs)
