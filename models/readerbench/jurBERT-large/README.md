Model card for jurBERT-large

---
language: 
- ro
---

# jurBERT-large


## Pretrained juridical BERT model for Romanian 

BERT Romanian juridical model trained using a masked language modeling (MLM) and next sentence prediction (NSP) objective. 
It was introduced in this [paper](https://aclanthology.org/2021.nllp-1.8/). Two BERT models were released: **jurBERT-base** and **jurBERT-large**, all versions uncased.

| Model          | Weights   |   L    |   H    |    A   | MLM accuracy   | NSP accuracy   |
|----------------|:---------:|:------:|:------:|:------:|:--------------:|:--------------:|
| jurBERT-base    | 111M      | 12     | 768    | 12     | 0.8936         | 0.9923         |
| *jurBERT-large*   | *337M*  | *24*     | *1024*   | *24*     | *0.9005*         | *0.9929*         |




All models are available:

* [jurBERT-base](https://huggingface.co/readerbench/jurBERT-base)
* [jurBERT-large](https://huggingface.co/readerbench/jurBERT-large)



#### How to use

```python
# tensorflow
from transformers import AutoModel, AutoTokenizer, TFAutoModel
tokenizer = AutoTokenizer.from_pretrained("readerbench/jurBERT-large")
model = TFAutoModel.from_pretrained("readerbench/jurBERT-large")
inputs = tokenizer("exemplu de propoziție", return_tensors="tf")
outputs = model(inputs)


# pytorch
from transformers import AutoModel, AutoTokenizer, AutoModel
tokenizer = AutoTokenizer.from_pretrained("readerbench/jurBERT-large")
model = AutoModel.from_pretrained("readerbench/jurBERT-large")
inputs = tokenizer("exemplu de propoziție", return_tensors="pt")
outputs = model(**inputs)
```


## Datasets

The model is trained on a private corpus (that can nevertheless be rented for a fee), that is comprised of all the final ruling, containing both civil and criminal cases, published by any Romanian civil court between 2010 and 2018. Validation is performed on RoBanking datase. We extracted from RoJur common types of cases pertinent to the banking domain (e.g. administration fee litigations, enforcement appeals), kept only the summary of the arguments provided by both the plaitiffs and the defendants and the final verdict (in the form of a boolean value) to build RoBanking. 

| Corpus    | Scope        |Entries    |  Size (GB)|
|-----------|:------------:|:---------:|:---------:|
| RoJur     | pre-training | 11M       | 160       |
| RoBanking | downstream   | 108k      | -         |


## Downstream performance

We report Mean AUC and Std AUC on the task of predicting the outcome of a case. 

### Results on RoBanking using only the plea of the plaintiff.

| Model              | Mean AUC | Std AUC  |
|--------------------|:--------:|:--------:|
| CNN                | 79.60    | -        |
| BI-LSTM            | 80.99    | 0.26     |
| RoBERT-small       | 70.54    | 0.28     |
| RoBERT-base        | 79.74    | 0.21     |
| RoBERT-base + hf   | 79.82    | 0.11     |
| RoBERT-large       | 76.53    | 5.43     |
| jurBERT-base       | **81.47**| **0.18** |
| jurBERT-base + hf  | 81.40    | 0.18     |
| *jurBERT-large*    | *78.38*  | *1.77*   |

### Results on RoBanking using pleas from both the plaintiff and defendant.

| Model               | Mean AUC | Std AUC  |
|---------------------|:--------:|:--------:|
| BI-LSTM             | 84.60    | 0.59     |
| RoBERT-base         | 84.40    | 0.26     |
| RoBERT-base + hf    | 84.43    | 0.15     |
| jurBERT-base        | 86.63    | 0.18     |
| jurBERT-base + hf   | **86.73**| **0.22** |
| *jurBERT-large*     | *82.04*  | *0.64*    |


For complete results and discussion please refer to the [paper](https://aclanthology.org/2021.nllp-1.8/).

### BibTeX entry and citation info

```bibtex
@inproceedings{masala2021jurbert,
  title={jurBERT: A Romanian BERT Model for Legal Judgement Prediction},
  author={Masala, Mihai and Iacob, Radu Cristian Alexandru and Uban, Ana Sabina and Cidota, Marina and Velicu, Horia and Rebedea, Traian and Popescu, Marius},
  booktitle={Proceedings of the Natural Legal Language Processing Workshop 2021},
  pages={86--94},
  year={2021}
}
```

