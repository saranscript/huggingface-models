---
language:
- ru
tags:
- sentiment
- text-classification
datasets:
- Tatyana/ru_sentiment_dataset
---

# RuBERT for Sentiment Analysis
Russian texts sentiment classification.

Model trained on [Tatyana/ru_sentiment_dataset](https://huggingface.co/datasets/Tatyana/ru_sentiment_dataset)

## Labels meaning
    0: NEUTRAL
    1: POSITIVE
    2: NEGATIVE

## How to use
```python

!pip install tensorflow-gpu
!pip install deeppavlov
!python -m deeppavlov install squad_bert
!pip install fasttext
!pip install transformers
!python -m deeppavlov install bert_sentence_embedder

from deeppavlov import build_model

model = build_model(path_to_model/rubert_sentiment.json)
model(["Сегодня хорошая погода", "Я счастлив проводить с тобою время", "Мне нравится эта музыкальная композиция"])

```

Needed pytorch trained model presented in [Drive](https://drive.google.com/drive/folders/1EnJBq0dGfpjPxbVjybqaS7PsMaPHLUIl?usp=sharing).

Load and place model.pth.tar in folder next to another files of a model.
