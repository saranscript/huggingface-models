---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- severo/autonlp-data-sentiment_detection-3c8bcd36
---

# Model Trained Using AutoNLP

_debug - I want to update this model_

- Problem type: Binary Classification
- Model ID: 1781580

## Validation Metrics

- Loss: 0.16026505827903748
- Accuracy: 0.9426
- Precision: 0.9305057745917961
- Recall: 0.95406288280931
- AUC: 0.9861051024994563
- F1: 0.9421370967741935

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/severo/autonlp-sentiment_detection-1781580
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("severo/autonlp-sentiment_detection-1781580", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("severo/autonlp-sentiment_detection-1781580", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```