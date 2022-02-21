---
language: uz
tags:
- uzbert
- uzbek
- bert
- cyrillic
license: mit
datasets:
- webcrawl
---

# UzBERT base model (uncased)

Pretrained model on Uzbek language (Cyrillic script) using a masked
language modeling and next sentence prediction objectives.

## How to use

You can use this model directly with a pipeline for masked language modeling:

```python
>>> from transformers import pipeline
>>> unmasker = pipeline('fill-mask', model='coppercitylabs/uzbert-base-uncased')
>>> unmasker("Алишер Навоий – улуғ ўзбек ва бошқа туркий халқларнинг [MASK], мутафаккири ва давлат арбоби бўлган.")

[
    {
        'token_str': 'шоири',
        'token': 13587,
        'score': 0.7974384427070618,
        'sequence': 'алишер навоий – улуғ ўзбек ва бошқа туркий халқларнинг шоири, мутафаккир ##и ва давлат арбоби бўлган.'
    },
    {
        'token_str': 'олими',
        'token': 18500,
        'score': 0.09166576713323593,
        'sequence': 'алишер навоий – улуғ ўзбек ва бошқа туркий халқларнинг олими, мутафаккир ##и ва давлат арбоби бўлган.'
    },
    {
        'token_str': 'асосчиси',
        'token': 7469,
        'score': 0.02451123297214508,
        'sequence': 'алишер навоий – улуғ ўзбек ва бошқа туркий халқларнинг асосчиси, мутафаккир ##и ва давлат арбоби бўлган.'
    },
    {
        'token_str': 'ёзувчиси',
        'token': 22439,
        'score': 0.017601722851395607,
        'sequence': 'алишер навоий – улуғ ўзбек ва бошқа туркий халқларнинг ёзувчиси, мутафаккир ##и ва давлат арбоби бўлган.'
    },
    {
        'token_str': 'устози',
        'token': 11494,
        'score': 0.010115668177604675,
        'sequence': 'алишер навоий – улуғ ўзбек ва бошқа туркий халқларнинг устози, мутафаккир ##и ва давлат арбоби бўлган.'
    }
]
```

## Training data

UzBERT model was pretrained on \~625K news articles (\~142M words).

## BibTeX entry and citation info
```bibtex
@misc{mansurov2021uzbert,
      title={{UzBERT: pretraining a BERT model for Uzbek}},
      author={B. Mansurov and A. Mansurov},
      year={2021},
      eprint={2108.09814},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```
