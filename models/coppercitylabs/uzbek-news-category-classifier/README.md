---
language: uz
tags:
- uzbek
- cyrillic
- news category classifier
license: mit
datasets:
- webcrawl
---

# Uzbek news category classifier (based on UzBERT)

UzBERT fine-tuned to classify news articles into one of the following
categories:

- дунё
- жамият
- жиноят
- иқтисодиёт
- маданият
- реклама
- саломатлик
- сиёсат
- спорт
- фан ва техника
- шоу-бизнес

## How to use

```python
>>> from transformers import pipeline
>>> classifier = pipeline('text-classification', model='coppercitylabs/uzbek-news-category-classifier')
>>> text = """Маҳоратли пара-енгил атлетикачимиз Ҳусниддин Норбеков Токио-2020 Паралимпия ўйинларида ғалаба қозониб, делегациямиз ҳисобига навбатдаги олтин медални келтирди. Бу ҳақда МОҚ хабар берди.

Норбеков ҳозиргина ядро улоқтириш дастурида ўз ғалабасини тантана қилди. Ушбу машқда вакилимиз 16:13 метр натижа билан энг яхши кўрсаткични қайд этди.

Шу тариқа, делегациямиз ҳисобидаги медаллар сони 16 (6 та олтин, 4 та кумуш ва 6 та бронза) тага етди. Кейинги кун дастурларида иштирок этадиган ҳамюртларимизга омад тилаб қоламиз!﻿"""
>>> classifier(text)
[{'label': 'спорт', 'score': 0.9865401983261108}]
```

## Fine-tuning data
Fine-tuned on ~60K news articles for 3 epochs.
