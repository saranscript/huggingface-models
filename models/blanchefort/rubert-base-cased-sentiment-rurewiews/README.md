---
language:
- ru
tags:
- sentiment
- text-classification
datasets:
- RuReviews
---

# RuBERT for Sentiment Analysis of Product Reviews

This is a [DeepPavlov/rubert-base-cased-conversational](https://huggingface.co/DeepPavlov/rubert-base-cased-conversational) model trained on [RuReviews](https://github.com/sismetanin/rureviews).

## Labels
    0: NEUTRAL
    1: POSITIVE
    2: NEGATIVE

## How to use
```python

import torch
from transformers import AutoModelForSequenceClassification
from transformers import BertTokenizerFast

tokenizer = BertTokenizerFast.from_pretrained('blanchefort/rubert-base-cased-sentiment-rurewiews')
model = AutoModelForSequenceClassification.from_pretrained('blanchefort/rubert-base-cased-sentiment-rurewiews', return_dict=True)

@torch.no_grad()
def predict(text):
    inputs = tokenizer(text, max_length=512, padding=True, truncation=True, return_tensors='pt')
    outputs = model(**inputs)
    predicted = torch.nn.functional.softmax(outputs.logits, dim=1)
    predicted = torch.argmax(predicted, dim=1).numpy()
    return predicted
```


## Dataset used for model training

**[RuReviews](https://github.com/sismetanin/rureviews)**

> RuReviews: An Automatically Annotated Sentiment Analysis Dataset for Product Reviews in Russian.
