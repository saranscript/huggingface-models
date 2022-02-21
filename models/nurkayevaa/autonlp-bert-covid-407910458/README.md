---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- nurkayevaa/autonlp-data-bert-covid
co2_eq_emissions: 9.72797586719897
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 407910458
- CO2 Emissions (in grams): 9.72797586719897

## Validation Metrics

- Loss: 0.20907048881053925
- Accuracy: 0.9119825708061002
- Precision: 0.8912721893491125
- Recall: 0.9563492063492064
- AUC: 0.9698454873092555
- F1: 0.9226646248085759

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/nurkayevaa/autonlp-bert-covid-407910458
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("nurkayevaa/autonlp-bert-covid-407910458", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("nurkayevaa/autonlp-bert-covid-407910458", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```