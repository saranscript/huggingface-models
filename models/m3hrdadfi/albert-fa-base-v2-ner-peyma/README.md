---
language: fa
license: apache-2.0
---

# ALBERT Persian

A Lite BERT for Self-supervised Learning of Language Representations for the Persian Language

> میتونی بهش بگی برت_کوچولو

[ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) is the first attempt on ALBERT for the Persian Language. The model was trained based on Google's ALBERT BASE Version 2.0 over various writing styles from numerous subjects (e.g., scientific, novels, news) with more than 3.9M documents, 73M sentences, and 1.3B words, like the way we did for ParsBERT.

Please follow the [ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) repo for the latest information about previous and current models.

## Persian NER [ARMAN, PEYMA]

This task aims to extract named entities in the text, such as names and label with appropriate `NER` classes such as locations, organizations, etc. The datasets used for this task contain sentences that are marked with `IOB` format. In this format, tokens that are not part of an entity are tagged as `”O”` the `”B”`tag corresponds to the first word of an object, and the `”I”` tag corresponds to the rest of the terms of the same entity. Both `”B”` and `”I”` tags are followed by a hyphen (or underscore), followed by the entity category. Therefore, the NER task is a multi-class token classification problem that labels the tokens upon being fed a raw text. There are two primary datasets used in Persian NER, `ARMAN`, and `PEYMA`.

### PEYMA

PEYMA dataset includes 7,145 sentences with a total of 302,530 tokens from which 41,148 tokens are tagged with seven different classes.

1. Organization
2. Money
3. Location
4. Date
5. Time
6. Person
7. Percent


|     Label    |   #   |
|:------------:|:-----:|
| Organization | 16964 |
|     Money    |  2037 |
|   Location   |  8782 |
|     Date     |  4259 |
|     Time     |  732  |
|    Person    |  7675 |
|    Percent   |  699  |


**Download**
You can download the dataset from [here](http://nsurl.org/tasks/task-7-named-entity-recognition-ner-for-farsi/)


## Results

The following table summarizes the F1 score obtained as compared to other models and architectures.

| Dataset | ALBERT-fa-base-v2 | ParsBERT-v1 | mBERT | MorphoBERT | Beheshti-NER | LSTM-CRF | Rule-Based CRF | BiLSTM-CRF |
|:-------:|:-----------------:|:-----------:|:-----:|:----------:|:------------:|:--------:|:--------------:|:----------:|
|  PEYMA  |       88.99       |    93.10    | 86.64 |      -     |     90.59    |     -    |      84.00     |      -     |


### BibTeX entry and citation info

Please cite in publications as the following:

```bibtex
@misc{ALBERTPersian,
  author = {Mehrdad Farahani},
  title = {ALBERT-Persian: A Lite BERT for Self-supervised Learning of Language Representations for the Persian Language},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/m3hrdadfi/albert-persian}},
}

@article{ParsBERT,
    title={ParsBERT: Transformer-based Model for Persian Language Understanding},
    author={Mehrdad Farahani, Mohammad Gharachorloo, Marzieh Farahani, Mohammad Manthouri},
    journal={ArXiv},
    year={2020},
    volume={abs/2005.12515}
}
```

## Questions?
Post a Github issue on the [ALBERT-Persian](https://github.com/m3hrdadfi/albert-persian) repo.