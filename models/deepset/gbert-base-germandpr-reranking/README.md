---
language: de
datasets:
- deepset/germandpr
license: mit
---

## Overview
**Language model:** gbert-base-germandpr-reranking  
**Language:** German  
**Training data:** GermanDPR train set (~ 56MB)  
**Eval data:** GermanDPR test set (~ 6MB)   
**Infrastructure**: 1x V100 GPU  
**Published**: June 3rd, 2021

## Details
- We trained a text pair classification model in FARM, which can be used for reranking in document retrieval tasks. To this end, the classifier calculates the similarity of the query and each retrieved top k document (e.g., k=10). The top k documents are then sorted by their similarity scores. The document most similar to the query is the best.

## Hyperparameters
```
batch_size = 16
n_epochs = 2
max_seq_len = 512 tokens for question and passage concatenated
learning_rate = 2e-5
lr_schedule = LinearWarmup
embeds_dropout_prob = 0.1
```
## Performance
We use the GermanDPR test dataset as ground truth labels and run two experiments to compare how a BM25 retriever performs with or without reranking with our model. The first experiment runs retrieval on the full German Wikipedia (more than 2 million passages) and second experiment runs retrieval on the GermanDPR dataset only (not more than 5000 passages). Both experiments use 1025 queries. Note that the second experiment is evaluating on a much simpler task because of the smaller dataset size, which explains strong BM25 retrieval performance.

### Full German Wikipedia (more than 2 million passages):
BM25 Retriever without Reranking
- recall@3: 0.4088 (419 / 1025)
- mean_reciprocal_rank@3: 0.3322

BM25 Retriever with Reranking Top 10 Documents
- recall@3: 0.5200 (533 / 1025)
- mean_reciprocal_rank@3: 0.4800

### GermanDPR Test Dataset only (not more than 5000 passages):
BM25 Retriever without Reranking
- recall@3: 0.9102 (933 / 1025)
- mean_reciprocal_rank@3: 0.8528

BM25 Retriever with Reranking Top 10 Documents
- recall@3: 0.9298 (953 / 1025)
- mean_reciprocal_rank@3: 0.8813



## Usage
### In haystack
You can load the model in [haystack](https://github.com/deepset-ai/haystack/) for reranking the documents returned by a Retriever:
```python
...
retriever = ElasticsearchRetriever(document_store=document_store)
ranker = FARMRanker(model_name_or_path="deepset/gbert-base-germandpr-reranking")
...
p = Pipeline()
p.add_node(component=retriever, name="ESRetriever", inputs=["Query"])
p.add_node(component=ranker, name="Ranker", inputs=["ESRetriever"])
)
```

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
