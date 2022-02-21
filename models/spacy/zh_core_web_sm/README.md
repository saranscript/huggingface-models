---
tags:
- spacy
- token-classification
language:
- zh
license: mit
model-index:
- name: zh_core_web_sm
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.7224990884
    - name: NER Recall
      type: recall
      value: 0.6531868132
    - name: NER F Score
      type: f_score
      value: 0.6860968431
  - task:
      name: POS
      type: token-classification
    metrics:
    - name: POS Accuracy
      type: accuracy
      value: 0.8957464158
  - task:
      name: SENTER
      type: token-classification
    metrics:
    - name: SENTER Precision
      type: precision
      value: 0.7817728729
    - name: SENTER Recall
      type: recall
      value: 0.7311469952
    - name: SENTER F Score
      type: f_score
      value: 0.7556129032
  - task:
      name: UNLABELED_DEPENDENCIES
      type: token-classification
    metrics:
    - name: Unlabeled Dependencies Accuracy
      type: accuracy
      value: 0.6965379684
  - task:
      name: LABELED_DEPENDENCIES
      type: token-classification
    metrics:
    - name: Labeled Dependencies Accuracy
      type: accuracy
      value: 0.6965379684
---
### Details: https://spacy.io/models/zh#zh_core_web_sm

Chinese pipeline optimized for CPU. Components: tok2vec, tagger, parser, senter, ner, attribute_ruler.

| Feature | Description |
| --- | --- |
| **Name** | `zh_core_web_sm` |
| **Version** | `3.2.0` |
| **spaCy** | `>=3.2.0,<3.3.0` |
| **Default Pipeline** | `tok2vec`, `tagger`, `parser`, `attribute_ruler`, `ner` |
| **Components** | `tok2vec`, `tagger`, `parser`, `senter`, `attribute_ruler`, `ner` |
| **Vectors** | 0 keys, 0 unique vectors (0 dimensions) |
| **Sources** | [OntoNotes 5](https://catalog.ldc.upenn.edu/LDC2013T19) (Ralph Weischedel, Martha Palmer, Mitchell Marcus, Eduard Hovy, Sameer Pradhan, Lance Ramshaw, Nianwen Xue, Ann Taylor, Jeff Kaufman, Michelle Franchini, Mohammed El-Bachouti, Robert Belvin, Ann Houston)<br />[CoreNLP Universal Dependencies Converter](https://nlp.stanford.edu/software/stanford-dependencies.html) (Stanford NLP Group) |
| **License** | `MIT` |
| **Author** | [Explosion](https://explosion.ai) |

### Label Scheme

<details>

<summary>View label scheme (101 labels for 4 components)</summary>

| Component | Labels |
| --- | --- |
| **`tagger`** | `AD`, `AS`, `BA`, `CC`, `CD`, `CS`, `DEC`, `DEG`, `DER`, `DEV`, `DT`, `ETC`, `FW`, `IJ`, `INF`, `JJ`, `LB`, `LC`, `M`, `MSP`, `NN`, `NR`, `NT`, `OD`, `ON`, `P`, `PN`, `PU`, `SB`, `SP`, `URL`, `VA`, `VC`, `VE`, `VV`, `X` |
| **`parser`** | `ROOT`, `acl`, `advcl:loc`, `advmod`, `advmod:dvp`, `advmod:loc`, `advmod:rcomp`, `amod`, `amod:ordmod`, `appos`, `aux:asp`, `aux:ba`, `aux:modal`, `aux:prtmod`, `auxpass`, `case`, `cc`, `ccomp`, `compound:nn`, `compound:vc`, `conj`, `cop`, `dep`, `det`, `discourse`, `dobj`, `etc`, `mark`, `mark:clf`, `name`, `neg`, `nmod`, `nmod:assmod`, `nmod:poss`, `nmod:prep`, `nmod:range`, `nmod:tmod`, `nmod:topic`, `nsubj`, `nsubj:xsubj`, `nsubjpass`, `nummod`, `parataxis:prnmod`, `punct`, `xcomp` |
| **`senter`** | `I`, `S` |
| **`ner`** | `CARDINAL`, `DATE`, `EVENT`, `FAC`, `GPE`, `LANGUAGE`, `LAW`, `LOC`, `MONEY`, `NORP`, `ORDINAL`, `ORG`, `PERCENT`, `PERSON`, `PRODUCT`, `QUANTITY`, `TIME`, `WORK_OF_ART` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `TOKEN_ACC` | 97.88 |
| `TOKEN_P` | 94.58 |
| `TOKEN_R` | 91.36 |
| `TOKEN_F` | 92.94 |
| `TAG_ACC` | 89.57 |
| `SENTS_P` | 78.18 |
| `SENTS_R` | 73.11 |
| `SENTS_F` | 75.56 |
| `DEP_UAS` | 69.65 |
| `DEP_LAS` | 64.26 |
| `ENTS_P` | 72.25 |
| `ENTS_R` | 65.32 |
| `ENTS_F` | 68.61 |