---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- bozelosp/autonlp-data-sci-relevance
co2_eq_emissions: 3.667033499762825
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 33199029
- CO2 Emissions (in grams): 3.667033499762825

## Validation Metrics

- Loss: 0.32653310894966125
- Accuracy: 0.9133333333333333
- Precision: 0.9005847953216374
- Recall: 0.9447852760736196
- AUC: 0.9532488468944517
- F1: 0.9221556886227544

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/bozelosp/autonlp-sci-relevance-33199029
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("bozelosp/autonlp-sci-relevance-33199029", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("bozelosp/autonlp-sci-relevance-33199029", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```