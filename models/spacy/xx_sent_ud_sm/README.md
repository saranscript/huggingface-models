---
tags:
- spacy
language:
- multilingual
license: cc-by-sa-4.0
model-index:
- name: xx_sent_ud_sm
  results:
  - task:
      name: SENTER
      type: token-classification
    metrics:
    - name: SENTER Precision
      type: precision
      value: 0.9029477287
    - name: SENTER Recall
      type: recall
      value: 0.8194977584
    - name: SENTER F Score
      type: f_score
      value: 0.8592012289
---
### Details: https://spacy.io/models/xx#xx_sent_ud_sm

Multi-language pipeline optimized for CPU. Components: senter.

| Feature | Description |
| --- | --- |
| **Name** | `xx_sent_ud_sm` |
| **Version** | `3.1.0` |
| **spaCy** | `>=3.1.0,<3.2.0` |
| **Default Pipeline** | `senter` |
| **Components** | `senter` |
| **Vectors** | 0 keys, 0 unique vectors (0 dimensions) |
| **Sources** | [Universal Dependencies v2.5 (UD_Afrikaans-AfriBooms, UD_Croatian-SET, UD_Czech-CAC, UD_Czech-CLTT, UD_Danish-DDT, UD_Dutch-Alpino, UD_Dutch-LassySmall, UD_English-EWT, UD_Finnish-FTB, UD_Finnish-TDT, UD_French-GSD, UD_French-Spoken, UD_German-GSD, UD_Indonesian-GSD, UD_Irish-IDT, UD_Italian-TWITTIRO, UD_Korean-GSD, UD_Korean-Kaist, UD_Latvian-LVTB, UD_Lithuanian-ALKSNIS, UD_Lithuanian-HSE, UD_Marathi-UFAL, UD_Norwegian-Bokmaal, UD_Norwegian-Nynorsk, UD_Norwegian-NynorskLIA, UD_Persian-Seraji, UD_Portuguese-Bosque, UD_Portuguese-GSD, UD_Romanian-Nonstandard, UD_Romanian-RRT, UD_Russian-GSD, UD_Russian-Taiga, UD_Serbian-SET, UD_Slovak-SNK, UD_Spanish-GSD, UD_Swedish-Talbanken, UD_Telugu-MTG, UD_Vietnamese-VTB)](https://universaldependencies.org/) (Zeman, Daniel; Nivre, Joakim; Abrams, Mitchell; et al.) |
| **License** | `CC BY-SA 3.0` |
| **Author** | [Explosion](https://explosion.ai) |

### Label Scheme

<details>

<summary>View label scheme (2 labels for 1 components)</summary>

| Component | Labels |
| --- | --- |
| **`senter`** | `I`, `S` |

</details>

### Accuracy

| Type | Score |
| --- | --- |
| `TOKEN_ACC` | 99.29 |
| `SENTS_P` | 90.29 |
| `SENTS_R` | 81.95 |
| `SENTS_F` | 85.92 |
