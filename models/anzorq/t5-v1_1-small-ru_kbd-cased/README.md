---
language:
- ru
- kbd
tags:
- translation
datasets:
- anzorq/kbd-ru-1.67M-temp
- 17753 Russian-Kabardian pairs of text
widget:
- text: "ru->kbd: Я иду домой."
  example_title: "Я иду домой."
- text: "ru->kbd: Дети играют во дворе."
  example_title: "Дети играют во дворе."
- text: "ru->kbd: Сколько тебе лет?"
  example_title: "Сколько тебе лет?"
---

## [google/t5-v1_1-small](google/t5-v1_1-small) model
### pretrained on [anzorq/kbd-ru-1.67M-temp](https://huggingface.co/datasets/anzorq/kbd-ru-1.67M-temp)
### fine-tuned on **17753** Russian-Kabardian word/sentence pairs

kbd text uses custom latin script for optimization reasons.

Translation input should start with '**ru->kbd:** '.

**Tokenizer**: T5 sentencepiece, char, cased.