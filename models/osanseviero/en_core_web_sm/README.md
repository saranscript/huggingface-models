---
tags:
- token-classification
language:
- en
library_name: generic
license: MIT
model-index:
- name: en_core_web_sm
  results:
  - tasks:
      name: NER
      type: token-classification
      metrics:
      - name: Precision
        type: precision
        value: 0.8424355924
      - name: Recall
        type: recall
        value: 0.8335336538
      - name: F Score
        type: f_score
        value: 0.8379609817
  - tasks:
      name: POS
      type: token-classification
      metrics:
      - name: Accuracy
        type: accuracy
        value: 0.9720712187
  - tasks:
      name: SENTER
      type: token-classification
      metrics:
      - name: Precision
        type: precision
        value: 0.9074955788
      - name: Recall
        type: recall
        value: 0.8801372122
      - name: F Score
        type: f_score
        value: 0.893607046
  - tasks:
      name: UNLABELED_DEPENDENCIES
      type: token-classification
      metrics:
      - name: Accuracy
        type: accuracy
        value: 0.9185392711
  - tasks:
      name: LABELED_DEPENDENCIES
      type: token-classification
      metrics:
      - name: Accuracy
        type: accuracy
        value: 0.9185392711
---
### Details: https://spacy.io/models/en#en_core_web_sm

English pipeline optimized for CPU. Components: tok2vec, tagger, parser, senter, ner, attribute_ruler, lemmatizer.

| Feature | Description |
| --- | --- |
| **Name** | `en_core_web_sm` |
| **Version** | `3.1.0` |
| **spaCy** | `>=3.1.0,<3.2.0` |
| **Default Pipeline** | `tok2vec`, `tagger`, `parser`, `attribute_ruler`, `lemmatizer`, `ner` |
| **Components** | `tok2vec`, `tagger`, `parser`, `senter`, `attribute_ruler`, `lemmatizer`, `ner` |
| **Vectors** | 0 keys, 0 unique vectors (0 dimensions) |
| **Sources** | [OntoNotes 5](https://catalog.ldc.upenn.edu/LDC2013T19) (Ralph Weischedel, Martha Palmer, Mitchell Marcus, Eduard Hovy, Sameer Pradhan, Lance Ramshaw, Nianwen Xue, Ann Taylor, Jeff Kaufman, Michelle Franchini, Mohammed El-Bachouti, Robert Belvin, Ann Houston)<br />[ClearNLP Constituent-to-Dependency Conversion](https://github.com/clir/clearnlp-guidelines/blob/master/md/components/dependency_conversion.md) (Emory University)<br />[WordNet 3.0](https://wordnet.princeton.edu/) (Princeton University) |
| **License** | `MIT` |
| **Author** | [Explosion](https://explosion.ai) |

### Label Scheme

<details>

<summary>View label scheme (114 labels for 4 components)</summary>

| Component | Labels |
| --- | --- |
| **`tagger`** | `<!DOCTYPE html>
<html class=