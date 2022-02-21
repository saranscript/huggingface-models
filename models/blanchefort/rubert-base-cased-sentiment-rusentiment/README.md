---
language:
- ru
tags:
- sentiment
- text-classification
datasets:
- RuSentiment
---

# RuBERT for Sentiment Analysis

This is a [DeepPavlov/rubert-base-cased-conversational](https://huggingface.co/DeepPavlov/rubert-base-cased-conversational) model trained on [RuSentiment](http://text-machine.cs.uml.edu/projects/rusentiment/).

## Labels
    0: NEUTRAL
    1: POSITIVE
    2: NEGATIVE

## How to use
```python

import torch
from transformers import AutoModelForSequenceClassification
from transformers import BertTokenizerFast

tokenizer = BertTokenizerFast.from_pretrained('blanchefort/rubert-base-cased-sentiment-rusentiment')
model = AutoModelForSequenceClassification.from_pretrained('blanchefort/rubert-base-cased-sentiment-rusentiment', return_dict=True)

@torch.no_grad()
def predict(text):
    inputs = tokenizer(text, max_length=512, padding=True, truncation=True, return_tensors='pt')
    outputs = model(**inputs)
    predicted = torch.nn.functional.softmax(outputs.logits, dim=1)
    predicted = torch.argmax(predicted, dim=1).numpy()
    return predicted
```


## Dataset used for model training

**[RuSentiment](http://text-machine.cs.uml.edu/projects/rusentiment/)**

> A. Rogers A. Romanov A. Rumshisky S. Volkova M. Gronas A. Gribov RuSentiment: An Enriched Sentiment Analysis Dataset for Social Media in Russian. Proceedings of COLING 2018.