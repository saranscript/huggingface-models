---
language: 

  - en

tags:
- text-classification
- sentiment-analysis
- sentiment-classification
- targeted-sentiment-classification
- target-depentent-sentiment-classification

license: "apache-2.0"

datasets: "fhamborg/news_sentiment_newsmtsc"

---

# NewsSentiment: easy-to-use, high-quality target-dependent sentiment classification for news articles

## Important: [use our PyPI package](https://pypi.org/project/NewsSentiment/) instead of this model on the Hub
The Huggingface Hub architecture currently [does not support](https://github.com/huggingface/transformers/issues/14785) target-dependent sentiment classification since you cannot provide the required inputs, i.e., sentence and target. Thus, we recommend that you use our easy-to-use [PyPI package NewsSentiment](https://pypi.org/project/NewsSentiment/).

## Description

This model is the currently [best performing](https://aclanthology.org/2021.eacl-main.142.pdf) 
targeted sentiment classifier for news articles. In contrast to regular sentiment
classification, targeted sentiment classification allows you to provide a target in a sentence. 
Only for this target, the sentiment is then predicted. This is more reliable in many
cases, as demonstrated by the following simplistic example: "I like Bert, but I hate Robert."

This model is also available as an easy-to-use PyPI package named [`NewsSentiment`](https://pypi.org/project/NewsSentiment/) and 
in its original GitHub repository named [`NewsMTSC`](https://github.com/fhamborg/NewsMTSC), where you will find the dataset the model was trained on, other models for sentiment classification, and a training and testing framework. More information on the model and the dataset (consisting of more than 10k sentences sampled from news articles, each 
labeled and agreed upon by at least 5 annotators) can be found in our [EACL paper](https://aclanthology.org/2021.eacl-main.142.pdf). The
dataset, the model, and its source code can be viewed in our [GitHub repository](https://github.com/fhamborg/NewsMTSC).

We recommend to use our [PyPI package](https://pypi.org/project/NewsSentiment/) for sentiment classification since the Huggingface Hub platform seems to [not support](https://github.com/huggingface/transformers/issues/14785) target-dependent sentiment classification.


# How to cite
If you use the dataset or model, please cite our [paper](https://www.aclweb.org/anthology/2021.eacl-main.142/) ([PDF](https://www.aclweb.org/anthology/2021.eacl-main.142.pdf)):

```
@InProceedings{Hamborg2021b,
  author    = {Hamborg, Felix and Donnay, Karsten},
  title     = {NewsMTSC: (Multi-)Target-dependent Sentiment Classification in News Articles},
  booktitle = {Proceedings of the 16th Conference of the European Chapter of the Association for Computational Linguistics (EACL 2021)},
  year      = {2021},
  month     = {Apr.},
  location  = {Virtual Event},
}
```
