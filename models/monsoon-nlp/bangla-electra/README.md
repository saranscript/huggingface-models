---
language: bn
---

# Bangla-Electra

This is a second attempt at a Bangla/Bengali language model trained with
Google Research's [ELECTRA](https://github.com/google-research/electra).

Tokenization and pre-training CoLab: https://colab.research.google.com/drive/1gpwHvXAnNQaqcu-YNx1kafEVxz07g2jL

V1 - 120,000 steps; V2 - 190,000 steps

## Classification

Classification with SimpleTransformers: https://colab.research.google.com/drive/1vltPI81atzRvlALv4eCvEB0KdFoEaCOb

On Soham Chatterjee's [news classification task](https://github.com/soham96/Bangla2Vec):
(Random: 16.7%, mBERT: 72.3%, Bangla-Electra: 82.3%)

Similar to mBERT on some tasks and configurations described in https://arxiv.org/abs/2004.07807

## Question Answering

This model can be used for Question Answering - this notebook uses Bangla questions from Google's TyDi dataset:
https://colab.research.google.com/drive/1i6fidh2tItf_-IDkljMuaIGmEU6HT2Ar

## Corpus

Trained on a web crawl from https://oscar-corpus.com/ (deduped version, 5.8GB) and 1 July 2020 dump of bn.wikipedia.org (414MB)

## Vocabulary

Included as vocab.txt in the upload - vocab_size is 29898
