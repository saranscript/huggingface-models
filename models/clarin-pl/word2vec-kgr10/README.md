---
language: pl
tags:
- word2vec
datasets:
- KGR10
---

# KGR10 word2vec Polish word embeddings

Distributional language models for Polish trained on the KGR10 corpora.

## Models

In the repository you can find two selected models, that were selected after evaluation (see table below). 
A model that performed the best is the default model/config (see `default_config.json`). 

|method|dimension|hs|mwe||
|---|---|---|---| --- |
|cbow|300|false|true| <-- default |
|skipgram|300|true|true|


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

embedding = AutoFlairWordEmbedding.from_hub("clarin-pl/word2vec-kgr10")
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

embedding = AutoFlairDocumentEmbedding.from_hub("clarin-pl/word2vec-kgr10")
embedding.embed([sentence])

print(sentence.embedding)
```

### Customisable way

Word embedding:

```python
from embeddings.embedding.static.embedding import AutoStaticWordEmbedding
from embeddings.embedding.static.word2vec import KGR10Word2VecConfig
from flair.data import Sentence

config = KGR10Word2VecConfig(method='skipgram', hs=False)
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
from embeddings.embedding.static.word2vec import KGR10Word2VecConfig
from flair.data import Sentence

config = KGR10Word2VecConfig(method='skipgram', hs=False)
embedding = AutoStaticDocumentEmbedding.from_config(config)

sentence = Sentence("Myśl z duszy leci bystro, Nim się w słowach złamie.")
embedding.embed([sentence])

print(sentence.embedding)
```

## Citation

```
Piasecki, Maciej; Janz, Arkadiusz; Kaszewski, Dominik; et al., 2017,  Word Embeddings for Polish, CLARIN-PL digital repository, http://hdl.handle.net/11321/442.
```

or 


```
@misc{11321/442,	
 title = {Word Embeddings for Polish},	
 author = {Piasecki, Maciej and Janz, Arkadiusz and Kaszewski, Dominik and Czachor, Gabriela},	
 url = {http://hdl.handle.net/11321/442},	
 note = {{CLARIN}-{PL} digital repository},	
 copyright = {{GNU} {GPL3}},	
 year = {2017}	
}
```

