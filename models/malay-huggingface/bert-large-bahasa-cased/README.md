---
language: ms
---

# bert-large-bahasa-cased

Pretrained BERT large language model for Malay.

## Pretraining Corpus

`bert-large-bahasa-cased` model was pretrained on ~1.4 Billion words. Below is list of data we trained on,

1. [cleaned local texts](https://github.com/huseinzol05/malay-dataset/tree/master/dumping/clean).
2. [translated The Pile](https://github.com/huseinzol05/malay-dataset/tree/master/corpus/pile).

## Pretraining details

- All steps can reproduce from here, [Malaya/pretrained-model/bert](https://github.com/huseinzol05/Malaya/tree/master/pretrained-model/bert).

## Load Pretrained Model

You can use this model by installing `torch` or `tensorflow` and Huggingface library `transformers`. And you can use it directly by initializing it like this:  

```python
from transformers import BertTokenizer, BertModel

model = BertModel.from_pretrained('malay-huggingface/bert-large-bahasa-cased')
tokenizer = BertTokenizer.from_pretrained(
    'malay-huggingface/bert-large-bahasa-cased',
    do_lower_case = False,
)
```

## Example using AutoModelWithLMHead

```python
from transformers import BertTokenizer, BertForMaskedLM, pipeline

model = BertForMaskedLM.from_pretrained('malay-huggingface/bert-large-bahasa-cased')
tokenizer = BertTokenizer.from_pretrained(
    'malay-huggingface/bert-large-bahasa-cased',
    do_lower_case = False,
)
fill_mask = pipeline('fill-mask', model=model, tokenizer=tokenizer)
fill_mask('Permohonan Najib, anak untuk dengar isu perlembagaan [MASK] .')
```

Output is,

```text
[{'sequence': 'Permohonan Najib, anak untuk dengar isu perlembagaan Malaysia.',
  'score': 0.09178723394870758,
  'token': 1957,
  'token_str': 'M a l a y s i a'},
 {'sequence': 'Permohonan Najib, anak untuk dengar isu perlembagaan negara.',
  'score': 0.053524162620306015,
  'token': 2134,
  'token_str': 'n e g a r a'},
 {'sequence': 'Permohonan Najib, anak untuk dengar isu perlembagaan dikemukakan.',
  'score': 0.031137527897953987,
  'token': 9383,
  'token_str': 'd i k e m u k a k a n'},
 {'sequence': 'Permohonan Najib, anak untuk dengar isu perlembagaan 1MDB.',
  'score': 0.02826082520186901,
  'token': 13838,
  'token_str': '1 M D B'},
 {'sequence': 'Permohonan Najib, anak untuk dengar isu perlembagaan ditolak.',
  'score': 0.026568090543150902,
  'token': 11465,
  'token_str': 'd i t o l a k'}]
```


