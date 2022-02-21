---
tags:
- spacy
- token-classification
language:
- mk
license: cc-by-sa-4.0
model-index:
- name: mk_core_news_lg
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.7482876712
    - name: NER Recall
      type: recall
      value: 0.7438297872
    - name: NER F Score
      type: f_score
      value: 0.74605207
  - task:
      name: SENTER
      type: token-classification
    metrics:
    - name: SENTER Precision
      type: precision
      value: 0.6486486486
    - name: SENTER Recall
      type: recall
      value: 0.6233766234
    - name: SENTER F Score
      type: f_score
      value: 0.6357615894
  - task:
      name: UNLABELED_DEPENDENCIES
      type: token-classification
    metrics:
    - name: Unlabeled Dependencies Accuracy
      type: accuracy
      value: 0.6875612145
  - task:
      name: LABELED_DEPENDENCIES
      type: token-classification
    metrics:
    - name: Labeled Dependencies Accuracy
      type: accuracy
      value: 0.6875612145
---
### Details: https://spacy.io/models/mk#mk_core_news_lg

Macedonian pipeline optimized for CPU. Components: tok2vec, morphologizer, parser, senter, ner, attribute_ruler, lemmatizer.

| Feature | Description |
| --- | --- |
| **Name** | `mk_core_news_lg` |
| **Version** | `3.2.0` |
| **spaCy** | `>=3.2.0,<3.3.0` |
| **Default Pipeline** | `morphologizer`, `parser`, `attribute_ruler`, `lemmatizer`, `ner` |
| **Components** | `morphologizer`, `parser`, `senter`, `attribute_ruler`, `lemmatizer`, `ner` |
| **Vectors** | 274587 keys, 274587 unique vectors (300 dimensions) |
| **Sources** | [Macedonian Corpus](https://blog.netcetera.com/macedonian-spacy-f3c85484777f) (Damjan Zlatinov, Melanija Gerasimovska, Borijan Georgievski, Marija Todosovska)<br />[Macedonian Corpus](https://blog.netcetera.com/macedonian-spacy-f3c85484777f) (Damjan Zlatinov, Melanija Gerasimovska, Borijan Georgievski, Marija Todosovska)<br />[Macedonian Corpus](https://blog.netcetera.com/macedonian-spacy-f3c85484777f) (Damjan Zlatinov, Melanija Gerasimovska, Borijan Georgievski, Marija Todosovska)<br />[spaCy lookups data](https://github.com/explosion/spacy-lookups-data) (Explosion)<br />[Explosion fastText Vectors (cbow, OSCAR Common Crawl + Wikipedia)](https://spacy.io) (Explosion) |
| **License** | `CC BY-SA 4.0` |
| **Author** | [Explosion](https://explosion.ai) |

### Label Scheme

<details>

<summary>View label scheme (55 labels for 4 components)</summary>

| Component | Labels |
| --- | --- |
| **`morphologizer`** | `POS=PROPN`, `POS=AUX`, `POS=ADJ`, `POS=NOUN`, `POS=ADP`, `POS=PUNCT`, `POS=CONJ`, `POS=NUM`, `POS=VERB`, `POS=PRON`, `POS=ADV`, `POS=SCONJ`, `POS=PART`, `POS=SYM`, `POS=X`, `_`, `POS=INTJ` |
| **`parser`** | `ROOT`, `advmod`, `att`, `aux`, `cc`, `dep`, `det`, `dobj`, `iobj`, `neg`, `nsubj`, `pobj`, `poss`, `pozm`, `pozv`, `prep`, `punct`, `relcl` |
| **`senter`** | `I`, `S` |
| **`ner`** | `CARDINAL`, `DATE`, `EVENT`, `FAC`, `GPE`, `LANGUAGE`, `LAW`, `LOC`, `MONEY`, `NORP`, `ORDINAL`, `ORG`, `PERCENT`, `PERSON`, `PRODUCT`, `QUANTITY`, `TIME`, `WORK_OF_ART` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `TOKEN_ACC` | 100.00 |
| `TOKEN_P` | 100.00 |
| `TOKEN_R` | 100.00 |
| `TOKEN_F` | 100.00 |
| `SENTS_P` | 64.86 |
| `SENTS_R` | 62.34 |
| `SENTS_F` | 63.58 |
| `DEP_UAS` | 68.76 |
| `DEP_LAS` | 53.67 |
| `POS_ACC` | 93.39 |
| `ENTS_P` | 74.83 |
| `ENTS_R` | 74.38 |
| `ENTS_F` | 74.61 |