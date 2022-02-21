---
tags:
- spacy
- token-classification
language:
- ja
license: cc-by-sa-4.0
model-index:
- name: ja_core_news_md
  results:
  - task:
      name: NER
      type: token-classification
    metrics:
    - name: NER Precision
      type: precision
      value: 0.737704918
    - name: NER Recall
      type: recall
      value: 0.679245283
    - name: NER F Score
      type: f_score
      value: 0.7072691552
  - task:
      name: POS
      type: token-classification
    metrics:
    - name: POS Accuracy
      type: accuracy
      value: 0.9715755942
  - task:
      name: SENTER
      type: token-classification
    metrics:
    - name: SENTER Precision
      type: precision
      value: 0.9862475442
    - name: SENTER Recall
      type: recall
      value: 0.9901380671
    - name: SENTER F Score
      type: f_score
      value: 0.9881889764
  - task:
      name: UNLABELED_DEPENDENCIES
      type: token-classification
    metrics:
    - name: Unlabeled Dependencies Accuracy
      type: accuracy
      value: 0.9224188392
  - task:
      name: LABELED_DEPENDENCIES
      type: token-classification
    metrics:
    - name: Labeled Dependencies Accuracy
      type: accuracy
      value: 0.9224188392
---
### Details: https://spacy.io/models/ja#ja_core_news_md

Japanese pipeline optimized for CPU. Components: tok2vec, morphologizer, parser, senter, ner, attribute_ruler.

| Feature | Description |
| --- | --- |
| **Name** | `ja_core_news_md` |
| **Version** | `3.2.0` |
| **spaCy** | `>=3.2.0,<3.3.0` |
| **Default Pipeline** | `tok2vec`, `morphologizer`, `parser`, `attribute_ruler`, `ner` |
| **Components** | `tok2vec`, `morphologizer`, `parser`, `senter`, `attribute_ruler`, `ner` |
| **Vectors** | 480443 keys, 20000 unique vectors (300 dimensions) |
| **Sources** | [UD Japanese GSD v2.8](https://github.com/UniversalDependencies/UD_Japanese-GSD) (Omura, Mai; Miyao, Yusuke; Kanayama, Hiroshi; Matsuda, Hiroshi; Wakasa, Aya; Yamashita, Kayo; Asahara, Masayuki; Tanaka, Takaaki; Murawaki, Yugo; Matsumoto, Yuji; Mori, Shinsuke; Uematsu, Sumire; McDonald, Ryan; Nivre, Joakim; Zeman, Daniel)<br />[UD Japanese GSD v2.8 NER](https://github.com/megagonlabs/UD_Japanese-GSD) (Megagon Labs Tokyo)<br />[chiVe: Japanese Word Embedding with Sudachi & NWJC (chive-1.1-mc90-500k)](https://github.com/WorksApplications/chiVe) (Works Applications) |
| **License** | `CC BY-SA 4.0` |
| **Author** | [Explosion](https://explosion.ai) |

### Label Scheme

<details>

<summary>View label scheme (66 labels for 4 components)</summary>

| Component | Labels |
| --- | --- |
| **`morphologizer`** | `POS=NOUN`, `POS=ADP`, `POS=VERB`, `POS=SCONJ`, `POS=AUX`, `POS=PUNCT`, `POS=PART`, `POS=DET`, `POS=NUM`, `POS=ADV`, `POS=PRON`, `POS=ADJ`, `POS=PROPN`, `POS=CCONJ`, `POS=SYM`, `POS=NOUN\|Polarity=Neg`, `POS=AUX\|Polarity=Neg`, `POS=INTJ`, `POS=SCONJ\|Polarity=Neg` |
| **`parser`** | `ROOT`, `acl`, `advcl`, `advmod`, `amod`, `aux`, `case`, `cc`, `ccomp`, `compound`, `cop`, `csubj`, `dep`, `det`, `dislocated`, `fixed`, `mark`, `nmod`, `nsubj`, `nummod`, `obj`, `obl`, `punct` |
| **`senter`** | `I`, `S` |
| **`ner`** | `CARDINAL`, `DATE`, `EVENT`, `FAC`, `GPE`, `LANGUAGE`, `LAW`, `LOC`, `MONEY`, `MOVEMENT`, `NORP`, `ORDINAL`, `ORG`, `PERCENT`, `PERSON`, `PET_NAME`, `PHONE`, `PRODUCT`, `QUANTITY`, `TIME`, `TITLE_AFFIX`, `WORK_OF_ART` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `TOKEN_ACC` | 99.69 |
| `TOKEN_P` | 97.65 |
| `TOKEN_R` | 97.90 |
| `TOKEN_F` | 97.77 |
| `POS_ACC` | 97.13 |
| `MORPH_ACC` | 0.40 |
| `MORPH_MICRO_P` | 34.01 |
| `MORPH_MICRO_R` | 98.04 |
| `MORPH_MICRO_F` | 50.51 |
| `SENTS_P` | 98.62 |
| `SENTS_R` | 99.01 |
| `SENTS_F` | 98.82 |
| `DEP_UAS` | 92.24 |
| `DEP_LAS` | 90.75 |
| `TAG_ACC` | 97.16 |
| `LEMMA_ACC` | 96.59 |
| `ENTS_P` | 73.77 |
| `ENTS_R` | 67.92 |
| `ENTS_F` | 70.73 |