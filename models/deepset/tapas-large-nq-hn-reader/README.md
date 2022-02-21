---
language: en
tags:
- tapas
license: apache-2.0
---

This model contains the converted PyTorch checkpoint of the original Tensorflow model available in the [TaPas repository](https://github.com/google-research/tapas/blob/master/DENSE_TABLE_RETRIEVER.md#reader-models).
It is described in Herzig et al.'s (2021) [paper](https://aclanthology.org/2021.naacl-main.43/) _Open Domain Question Answering over Tables via Dense Retrieval_.

This model has 2 versions which can be used differing only in the table scoring head.
The default one has an adapted table scoring head in order to be able to generate probabilities out of the logits.
The other (non-default) version corredponds to the original checkpoint from the TaPas repository and can be accessed setting `revision="original"`.

# Usage
## In Haystack
If you want to use this model for question-answering over tables, you can load it in [Haystack](https://github.com/deepset-ai/haystack/):
```python
from haystack.nodes import TableReader

table_reader = TableReader(model_name_or_path="deepset/tapas-large-nq-hn-reader")
```
