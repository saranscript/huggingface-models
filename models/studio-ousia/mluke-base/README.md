---
language: multilingual
thumbnail: https://github.com/studio-ousia/luke/raw/master/resources/luke_logo.png
tags:
  - luke
  - named entity recognition
  - relation classification
  - question answering
license: apache-2.0
---

## mLUKE

**mLUKE** (multilingual LUKE) is a multilingual extension of LUKE.

Please check the [official repository](https://github.com/studio-ousia/luke) for
more details and updates.

This is the mLUKE base model with 12 hidden layers, 768 hidden size. The total number
of parameters in this model is 585M (278M for the word embeddings and encoder, 307M for the entity embeddings).
The model was initialized with the weights of XLM-RoBERTa(base) and trained using December 2020 version of Wikipedia in 24 languages.

### Citation

If you find mLUKE useful for your work, please cite the following paper:

```latex
@inproceedings{ri2021mluke,
  title={mLUKE: The Power of Entity Representations in Multilingual Pretrained Language Models},
  author={Ryokan Ri, Ikuya Yamada, Yoshimasa Tsuruoka},
  booktitle={arXiv},
  year={2021}
}
```
