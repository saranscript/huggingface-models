---
language: de
license: cc-by-sa-4.0
datasets:
  - germeval_14
tags:
  - German
  - de
  - NER
---
# BERT-DE-NER

## What is it?
This is a German BERT model fine-tuned for named entity recognition.

## Base model & training
This model is based on [bert-base-german-dbmdz-cased](https://huggingface.co/bert-base-german-dbmdz-cased) and has been fine-tuned
for NER on the training data from [GermEval2014](https://sites.google.com/site/germeval2014ner).

## Model results
The results on the test data from GermEval2014 are (entities only): 

| Precision | Recall | F1-Score |
|----------:|-------:|---------:|
|   0.817   |  0.842 |    0.829 |

## How to use
```Python
>>> from transformers import pipeline

>>> classifier = pipeline('ner', model="fhswf/bert_de_ner")
>>> classifier('Von der Organisation „medico international“ hieß es, die EU entziehe sich seit vielen Jahren der Verantwortung für die Menschen an ihren Außengrenzen.')

[{'word': 'med', 'score': 0.9996621608734131, 'entity': 'B-ORG', 'index': 6},
 {'word': '##ico', 'score': 0.9995362162590027, 'entity': 'I-ORG', 'index': 7},
 {'word': 'international',
  'score': 0.9996932744979858,
  'entity': 'I-ORG',
  'index': 8},
 {'word': 'eu', 'score': 0.9997008442878723, 'entity': 'B-ORG', 'index': 14}]

```
