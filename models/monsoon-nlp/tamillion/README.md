---
language: ta
---

# TaMillion

This is the second version of a Tamil language model trained with
Google Research's [ELECTRA](https://github.com/google-research/electra).

Tokenization and pre-training CoLab: https://colab.research.google.com/drive/1Pwia5HJIb6Ad4Hvbx5f-IjND-vCaJzSE?usp=sharing

V1: small model with GPU; 190,000 steps;

V2 (current): base model with TPU and larger corpus; 224,000 steps

## Classification

Sudalai Rajkumar's Tamil-NLP page contains classification and regression tasks:
https://www.kaggle.com/sudalairajkumar/tamil-nlp

Notebook: https://colab.research.google.com/drive/1_rW9HZb6G87-5DraxHvhPOzGmSMUc67_?usp=sharin

The model outperformed mBERT on news classification:
(Random: 16.7%, mBERT: 53.0%, TaMillion: 75.1%)

The model slightly outperformed mBERT on movie reviews:
(RMSE - mBERT: 0.657, TaMillion: 0.626)

Equivalent accuracy on the Tirukkural topic task.

## Question Answering

I didn't find a Tamil-language question answering dataset, but this model could be finetuned
to train a QA model. See Hindi and Bengali examples here: https://colab.research.google.com/drive/1i6fidh2tItf_-IDkljMuaIGmEU6HT2Ar

## Corpus

Trained on 
IndicCorp Tamil (11GB) https://indicnlp.ai4bharat.org/corpora/
and 1 October 2020 dump of https://ta.wikipedia.org (482MB)

## Vocabulary

Included as vocab.txt in the upload
