---
language: en
license: apache-2.0
---

# realm-cc-news-pretrained-encoder

## Model description

The REALM checkpoint pretrained with CC-News as target corpus and Wikipedia as knowledge corpus, converted from the TF checkpoint provided by Google Language.

The original paper, code, and checkpoints can be found [here](https://github.com/google-research/language/tree/master/language/realm).

## Usage

```python
from transformers import RealmKnowledgeAugEncoder

encoder = RealmKnowledgeAugEncoder.from_pretrained("qqaatw/realm-cc-news-pretrained-encoder")
```
