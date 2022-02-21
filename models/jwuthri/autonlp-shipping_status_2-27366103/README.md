---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- jwuthri/autonlp-data-shipping_status_2
co2_eq_emissions: 32.912881644048
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 27366103
- CO2 Emissions (in grams): 32.912881644048

## Validation Metrics

- Loss: 0.18175844848155975
- Accuracy: 0.9437683592110785
- Precision: 0.9416809605488851
- Recall: 0.8459167950693375
- AUC: 0.9815242330050846
- F1: 0.8912337662337663

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/jwuthri/autonlp-shipping_status_2-27366103
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("jwuthri/autonlp-shipping_status_2-27366103", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("jwuthri/autonlp-shipping_status_2-27366103", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```