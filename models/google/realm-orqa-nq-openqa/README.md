---
language: en
license: apache-2.0
---

# realm-orqa-nq-openqa

## Model description

The REALM checkpoint finetuned with Natural Questions(NQ) dataset, converted from the TF checkpoint provided by Google Language.

The original paper, code, and checkpoints can be found [here](https://github.com/google-research/language/tree/master/language/realm).

## Usage

```python
from transformers import RealmForOpenQA

openqa = RealmForOpenQA.from_pretrained("qqaatw/realm-orqa-nq-openqa")
```