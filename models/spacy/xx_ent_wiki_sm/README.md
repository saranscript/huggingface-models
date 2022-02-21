---
tags:
- spacy
- token-classification
language:
- multilingual
license: mit
model-index:
- name: xx_ent_wiki_sm
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.842542842
    - name: NER Recall
      type: recall
      value: 0.8348831014
    - name: NER F Score
      type: f_score
      value: 0.8386954831
---
### Details: https://spacy.io/models/xx#xx_ent_wiki_sm

Multi-language pipeline optimized for CPU. Components: ner.

| Feature | Description |
| --- | --- |
| **Name** | `xx_ent_wiki_sm` |
| **Version** | `3.2.0` |
| **spaCy** | `>=3.2.0,<3.3.0` |
| **Default Pipeline** | `ner` |
| **Components** | `ner` |
| **Vectors** | 0 keys, 0 unique vectors (0 dimensions) |
| **Sources** | [WikiNER](https://figshare.com/articles/Learning_multilingual_named_entity_recognition_from_Wikipedia/5462500) (Joel Nothman, Nicky Ringland, Will Radford, Tara Murphy, James R Curran) |
| **License** | `MIT` |
| **Author** | [Explosion](https://explosion.ai) |

### Label Scheme

<details>

<summary>View label scheme (4 labels for 1 components)</summary>

| Component | Labels |
| --- | --- |
| **`ner`** | `LOC`, `MISC`, `ORG`, `PER` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `ENTS_P` | 84.25 |
| `ENTS_R` | 83.49 |
| `ENTS_F` | 83.87 |