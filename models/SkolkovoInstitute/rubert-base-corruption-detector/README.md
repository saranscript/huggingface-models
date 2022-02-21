---
language: 
  - ru
tags:
  - fluency
---

This is a model for evaluation of naturalness of short Russian texts. It has been trained to distinguish human-written texts from their corrupted versions. 

Corruption sources: random replacement, deletion, addition, shuffling, and re-inflection of words and characters, random changes of capitalization, round-trip translation, filling random gaps with T5 and RoBERTA models. For each original text, we sampled three corrupted texts, so the model is uniformly biased towards the `unnatural` label.

Data sources: web-corpora from [the Leipzig collection](https://wortschatz.uni-leipzig.de/en/download) (`rus_news_2020_100K`, `rus_newscrawl-public_2018_100K`, `rus-ru_web-public_2019_100K`, `rus_wikipedia_2021_100K`), comments from [OK](https://www.kaggle.com/alexandersemiletov/toxic-russian-comments) and [Pikabu](https://www.kaggle.com/blackmoon/russian-language-toxic-comments).

On our private test dataset, the model has achieved 40% rank correlation with human judgements of naturalness, which is higher than GPT perplexity, another popular fluency metric.