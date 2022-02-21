---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- lucianpopa/autonlp-data-SST2
co2_eq_emissions: 8.883161797287569
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 551215591
- CO2 Emissions (in grams): 8.883161797287569

## Validation Metrics

- Loss: 0.08821876347064972
- Accuracy: 0.969531605275125
- Precision: 0.9734313841774404
- Recall: 0.9710127780407004
- AUC: 0.9949152422763072
- F1: 0.9722205769116863

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/lucianpopa/autonlp-SST2-551215591
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("lucianpopa/autonlp-SST2-551215591", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("lucianpopa/autonlp-SST2-551215591", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```