---
language:
- ru
tags:
- sentiment
- text-classification
---

# RuBERT for Sentiment Analysis of Medical Reviews

This is a [DeepPavlov/rubert-base-cased-conversational](https://huggingface.co/DeepPavlov/rubert-base-cased-conversational) model trained on corpus of medical reviews.

## Labels
    0: NEUTRAL
    1: POSITIVE
    2: NEGATIVE

## How to use
```python

import torch
from transformers import AutoModelForSequenceClassification
from transformers import BertTokenizerFast

tokenizer = BertTokenizerFast.from_pretrained('blanchefort/rubert-base-cased-sentiment-med')
model = AutoModelForSequenceClassification.from_pretrained('blanchefort/rubert-base-cased-sentiment-med', return_dict=True)

@torch.no_grad()
def predict(text):
    inputs = tokenizer(text, max_length=512, padding=True, truncation=True, return_tensors='pt')
    outputs = model(**inputs)
    predicted = torch.nn.functional.softmax(outputs.logits, dim=1)
    predicted = torch.argmax(predicted, dim=1).numpy()
    return predicted
```


## Dataset used for model training

**[Отзывы о медучреждениях](https://github.com/blanchefort/datasets/tree/master/medical_comments)**

> Датасет содержит пользовательские отзывы о медицинских учреждениях. Датасет собран в мае 2019 года с сайта prodoctorov.ru
