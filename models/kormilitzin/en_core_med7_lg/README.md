---
tags:
- spacy
- token-classification
language:
- en
license: mit
model-index:
- name: en_core_med7_lg
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.8778156997
    - name: NER Recall
      type: recall
      value: 0.8840918466
    - name: NER F Score
      type: f_score
      value: 0.8809425949
---
| Feature | Description |
| --- | --- |
| **Name** | `en_core_med7_lg` |
| **Version** | `3.1.3.1` |
| **spaCy** | `>=3.1.4,<3.2.0` |
| **Default Pipeline** | `tok2vec`, `ner` |
| **Components** | `tok2vec`, `ner` |
| **Vectors** | 684830 keys, 684830 unique vectors (300 dimensions) |
| **Sources** | n/a |
| **License** | `MIT` |
| **Author** | [Andrey Kormilitzin](kormilitzin.com) |

### Label Scheme

<details>

<summary>View label scheme (7 labels for 1 components)</summary>

| Component | Labels |
| --- | --- |
| **`ner`** | `DOSAGE`, `DRUG`, `DURATION`, `FORM`, `FREQUENCY`, `ROUTE`, `STRENGTH` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `ENTS_F` | 88.09 |
| `ENTS_P` | 87.78 |
| `ENTS_R` | 88.41 |
| `TOK2VEC_LOSS` | 115648.09 |
| `NER_LOSS` | 279069.77 |