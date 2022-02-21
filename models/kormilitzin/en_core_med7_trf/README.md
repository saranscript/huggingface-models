---
tags:
- spacy
- token-classification
language:
- en
license: mit
model-index:
- name: en_core_med7_trf
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.8910716705
    - name: NER Recall
      type: recall
      value: 0.9043035886
    - name: NER F Score
      type: f_score
      value: 0.8976388699
---
| Feature | Description |
| --- | --- |
| **Name** | `en_core_med7_trf` |
| **Version** | `3.1.3.1` |
| **spaCy** | `>=3.1.4,<3.2.0` |
| **Default Pipeline** | `transformer`, `ner` |
| **Components** | `transformer`, `ner` |
| **Vectors** | 0 keys, 0 unique vectors (0 dimensions) |
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
| `ENTS_F` | 89.76 |
| `ENTS_P` | 89.11 |
| `ENTS_R` | 90.43 |
| `TRANSFORMER_LOSS` | 209606.10 |
| `NER_LOSS` | 874893.84 |