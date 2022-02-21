---
language: en
tags:
- glossbert
license: mit
datasets:
- SemCor3.0
---

## GlossBERT

A BERT-based model fine-tuned on SemCor 3.0 to perform word-sense-disambiguation by leveraging gloss information. This model is the research output of the paper titled: '[GlossBERT: BERT for Word Sense Disambiguation with Gloss Knowledge](https://arxiv.org/pdf/1908.07245.pdf)'

Disclaimer: This model was built and trained by a group of researchers different than the repository's author. The original model code can be found on github: https://github.com/HSLCY/GlossBERT

## Usage

The following code loads GlossBERT:

```py
from transformers import AutoTokenizer, BertForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained('kanishka/GlossBERT')
model = BertForSequenceClassification.from_pretrained('kanishka/GlossBERT')
```

## Citation

If you use this model in any of your projects, please cite the original authors using the following bibtex:

```
@inproceedings{huang-etal-2019-glossbert,
    title = "{G}loss{BERT}: {BERT} for Word Sense Disambiguation with Gloss Knowledge",
    author = "Huang, Luyao  and
      Sun, Chi  and
      Qiu, Xipeng  and
      Huang, Xuanjing",
    booktitle = "Proceedings of the 2019 Conference on Empirical Methods in Natural Language Processing and the 9th International Joint Conference on Natural Language Processing (EMNLP-IJCNLP)",
    month = nov,
    year = "2019",
    address = "Hong Kong, China",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/D19-1355",
    doi = "10.18653/v1/D19-1355",
    pages = "3507--3512"
}
```