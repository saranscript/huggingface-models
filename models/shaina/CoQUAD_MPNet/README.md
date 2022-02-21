---
language: en
tags:
- MPNet

license: apache-2.0

dataset:
- covid-19
---

# CoQUAD_MPNet : MPNet model for COVID-19
## Introduction
It is a state-of-the-art language model for MPNet for Covid-19 dataset with focus on post-covid.
## How to use for Deepset Haystack

```python
# Load data

from datasets import load_dataset

dataset = load_dataset("shaina/covid19")

# Haystack pipeline
!sudo apt-get install git-lfs
!git lfs install
!git clone https://huggingface.co/shaina/CoQUAD_MPNet
GIT_LFS_SKIP_SMUDGE=1

from haystack.nodes import ElasticsearchRetriever
retriever = ElasticsearchRetriever(document_store=document_store)
reader = FARMReader(model_name_or_path="/content/drive/MyDrive/CoQUAD_MPNet", use_gpu=True)

from haystack.pipelines import ExtractiveQAPipeline
pipe = ExtractiveQAPipeline(reader, retriever)
prediction = pipe.run(
    query="What is post-COVID?", params={"Retriever": {"top_k": 10}, "Reader": {"top_k": 5}}
)
from pprint import pprint
pprint(prediction)
```
---
## Authors 
Shaina Raza

 ---