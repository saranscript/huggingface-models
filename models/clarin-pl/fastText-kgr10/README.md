---
language: pl
tags:
- fastText
datasets:
- kgr10
---

# KGR10 FastText Polish word embeddings

Distributional language model (both textual and binary) for Polish (word embeddings) trained on KGR10 corpus (over 4 billion of words) using Fasttext with the following variants (all possible combinations):
- dimension: 100, 300
- method: skipgram, cbow
- tool: FastText, Magnitude
- source text: plain, plain.lower, plain.lemma, plain.lemma.lower

## Models

In the repository you can find 4 selected models, that were examined in the paper (see Citation). 
A model that performed the best is the default model/config (see `default_config.json`).

## Usage

To use these embedding models easily, it is required to install [embeddings](https://github.com/CLARIN-PL/embeddings).

```bash
pip install clarinpl-embeddings
```

### Utilising the default model (the easiest way)

Word embedding:

```python
from embeddings.embedding.auto_flair import AutoFlairWordEmbedding
from flair.data import Sentence

sentence = Sentence("Myśl z duszy leci bystro, Nim się w słowach złamie.")

embedding = AutoFlairWordEmbedding.from_hub("clarin-pl/fastText-kgr10")
embedding.embed([sentence])

for token in sentence:
    print(token)
    print(token.embedding)
```

Document embedding (averaged over words):

```python
from embeddings.embedding.auto_flair import AutoFlairDocumentEmbedding
from flair.data import Sentence

sentence = Sentence("Myśl z duszy leci bystro, Nim się w słowach złamie.")

embedding = AutoFlairDocumentEmbedding.from_hub("clarin-pl/fastText-kgr10")
embedding.embed([sentence])

print(sentence.embedding)
```

### Customisable way

Word embedding:

```python
from embeddings.embedding.static.embedding import AutoStaticWordEmbedding
from embeddings.embedding.static.fasttext import KGR10FastTextConfig
from flair.data import Sentence

config = KGR10FastTextConfig(method='cbow', dimension=100)
embedding = AutoStaticWordEmbedding.from_config(config)

sentence = Sentence("Myśl z duszy leci bystro, Nim się w słowach złamie.")
embedding.embed([sentence])

for token in sentence:
    print(token)
    print(token.embedding)
```

Document embedding (averaged over words):

```python
from embeddings.embedding.static.embedding import AutoStaticDocumentEmbedding
from embeddings.embedding.static.fasttext import KGR10FastTextConfig
from flair.data import Sentence

config = KGR10FastTextConfig(method='cbow', dimension=100)
embedding = AutoStaticDocumentEmbedding.from_config(config)

sentence = Sentence("Myśl z duszy leci bystro, Nim się w słowach złamie.")
embedding.embed([sentence])

print(sentence.embedding)
```


## Citation

The link below leads to the NextCloud directory with all variants of embeddings. If you use it, please cite the following article:

```
@article{kocon2018embeddings,
author = {Koco\'{n}, Jan and Gawor, Micha{\l}},
title = {Evaluating {KGR10} {P}olish word embeddings in the recognition of temporal
expressions using {BiLSTM-CRF}},
journal = {Schedae Informaticae},
volume = {27},
year = {2018},
url = {http://www.ejournals.eu/Schedae-Informaticae/2018/Volume-27/art/13931/},
doi = {10.4467/20838476SI.18.008.10413}
}
```
