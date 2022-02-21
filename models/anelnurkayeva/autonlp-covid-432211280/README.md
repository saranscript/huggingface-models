---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- anelnurkayeva/autonlp-data-covid
co2_eq_emissions: 8.898145050355591
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 432211280
- CO2 Emissions (in grams): 8.898145050355591

## Validation Metrics

- Loss: 0.12489336729049683
- Accuracy: 0.9520089285714286
- Precision: 0.9436443331246086
- Recall: 0.9747736093143596
- AUC: 0.9910066767410616
- F1: 0.958956411072224

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/anelnurkayeva/autonlp-covid-432211280
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("anelnurkayeva/autonlp-covid-432211280", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("anelnurkayeva/autonlp-covid-432211280", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```