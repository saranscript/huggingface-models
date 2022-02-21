---
language: en

tags:
- sentence-embeddings
- sentence-similarity
- dual-encoder

### cambridgeltl/trans-encoder-bi-simcse-roberta-base
An unsupervised sentence encoder (bi-encoder) proposed by [Liu et al. (2021)](https://arxiv.org/pdf/2109.13059.pdf). The model is trained with unlabelled sentence pairs sampled from STS2012-2016, STS-b, and SICK-R, using [princeton-nlp/unsup-simcse-roberta-base](https://huggingface.co/princeton-nlp/unsup-simcse-roberta-base) as the base model. Please use `[CLS]` (before pooler) as the representation of the input.

### Citation
```bibtex
@article{liu2021trans,
  title={Trans-Encoder: Unsupervised sentence-pair modelling through self-and mutual-distillations},
  author={Liu, Fangyu and Jiao, Yunlong and Massiah, Jordan and Yilmaz, Emine and Havrylov, Serhii},
  journal={arXiv preprint arXiv:2109.13059},
  year={2021}
}
```
