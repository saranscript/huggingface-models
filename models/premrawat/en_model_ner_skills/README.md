---
tags:
- spacy
- token-classification
language:
- en
model-index:
- name: en_model_ner_skills
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.3063583815
    - name: NER Recall
      type: recall
      value: 0.2585365854
    - name: NER F Score
      type: f_score
      value: 0.2804232804
---
| Feature | Description |
| --- | --- |
| **Name** | `en_model_ner_skills` |
| **Version** | `0.0.0` |
| **spaCy** | `>=3.2.1,<3.3.0` |
| **Default Pipeline** | `tok2vec`, `ner` |
| **Components** | `tok2vec`, `ner` |
| **Vectors** | 0 keys, 0 unique vectors (0 dimensions) |
| **Sources** | n/a |
| **License** | n/a |
| **Author** | [n/a]() |

### Label Scheme

<details>

<summary>View label scheme (1 labels for 1 components)</summary>

| Component | Labels |
| --- | --- |
| **`ner`** | `SKILL` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `ENTS_F` | 28.04 |
| `ENTS_P` | 30.64 |
| `ENTS_R` | 25.85 |
| `TOK2VEC_LOSS` | 134572.33 |
| `NER_LOSS` | 133266.40 |