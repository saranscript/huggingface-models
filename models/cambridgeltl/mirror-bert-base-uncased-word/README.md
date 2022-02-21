---
language: en

tags:
- word-embeddings
- word-similarity

### mirror-bert-base-uncased-word
An unsupervised word encoder proposed by [Liu et al. (2021)](https://arxiv.org/pdf/2104.08027.pdf). Trained with a set of unlabelled words, using [bert-base-uncased](https://huggingface.co/bert-base-uncased) as the base model. Please use `[CLS]` as the representation of the input.

### Citation
```bibtex
@inproceedings{
	liu2021fast,
  title={Fast, Effective and Self-Supervised: Transforming Masked LanguageModels into Universal Lexical and Sentence Encoders},
  author={Liu, Fangyu and Vuli{\'c}, Ivan and Korhonen, Anna and Collier, Nigel},
  booktitle={EMNLP 2021},
  year={2021}
}
```
