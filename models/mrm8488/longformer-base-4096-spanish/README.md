---
language:
- es
license: mit
widget:
- text: "Manuel Romero ha creado con el equipo de BERTIN un modelo que procesa documentos <mask> largos."
tags:
- Long documents
- longformer
- bertin
- spanish
datasets:
- spanish_large_corpus

---

# longformer-base-4096-spanish

## [Longformer](https://arxiv.org/abs/2004.05150) is a Transformer model for long documents. 

`longformer-base-4096` is a BERT-like model started from the RoBERTa checkpoint (**BERTIN** in this case) and pre-trained for *MLM* on long documents (from BETO's `all_wikis`). It supports sequences of length up to 4,096! 

 

**Longformer** uses a combination of a sliding window (*local*) attention and *global* attention. Global attention is user-configured based on the task to allow the model to learn task-specific representations.


This model was made following the research done by [Iz Beltagy and Matthew E. Peters and Arman Cohan](https://arxiv.org/abs/2004.05150).