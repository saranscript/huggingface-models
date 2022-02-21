---
language:
- si
- en
tags:
- translation
license: apache-2.0
metrics:
- sacrebleu
---
# mt5-sinhalese-english

## Model description

An mT5-base model fine-tuned on the Sinhalese-English dataset in the Tatoeba Challenge. Can be used to translate from Sinhalese to English and vice versa.

## Training details
- English - Sinhala dataset from the Tatoeba Challenge [Datasets](https://github.com/Helsinki-NLP/Tatoeba-Challenge/blob/master/Data.md)
- [mT5-base pre-trained weights](https://huggingface.co/google/mt5-base)

## Eval results

SacreBLEU score:
- English to Sinhalese: 10.3
- Sinhalese to English: 24.4