---
language:
- en
- de
---
Our bibert-ende is a bilingual English-German Language Model. Please check out our EMNLP 2021 paper "[BERT, mBERT, or BiBERT? A Study on Contextualized Embeddings for Neural Machine Translation](https://aclanthology.org/2021.emnlp-main.534.pdf)" for more details.
```
@inproceedings{xu-etal-2021-bert,
    title = "{BERT}, m{BERT}, or {B}i{BERT}? A Study on Contextualized Embeddings for Neural Machine Translation",
    author = "Xu, Haoran  and
      Van Durme, Benjamin  and
      Murray, Kenton",
    booktitle = "Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2021",
    address = "Online and Punta Cana, Dominican Republic",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.emnlp-main.534",
    pages = "6663--6675",
    abstract = "The success of bidirectional encoders using masked language models, such as BERT, on numerous natural language processing tasks has prompted researchers to attempt to incorporate these pre-trained models into neural machine translation (NMT) systems. However, proposed methods for incorporating pre-trained models are non-trivial and mainly focus on BERT, which lacks a comparison of the impact that other pre-trained models may have on translation performance. In this paper, we demonstrate that simply using the output (contextualized embeddings) of a tailored and suitable bilingual pre-trained language model (dubbed BiBERT) as the input of the NMT encoder achieves state-of-the-art translation performance. Moreover, we also propose a stochastic layer selection approach and a concept of a dual-directional translation model to ensure the sufficient utilization of contextualized embeddings. In the case of without using back translation, our best models achieve BLEU scores of 30.45 for En→De and 38.61 for De→En on the IWSLT{'}14 dataset, and 31.26 for En→De and 34.94 for De→En on the WMT{'}14 dataset, which exceeds all published numbers.",
}
```
# Download

Note that tokenizer package is `BertTokenizer` not `AutoTokenizer`.
```
from transformers import BertTokenizer, AutoModel
tokenizer = BertTokenizer.from_pretrained("jhu-clsp/bibert-ende")
model = AutoModel.from_pretrained("jhu-clsp/bibert-ende")
```
