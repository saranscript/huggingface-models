---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- nurkayevaa/autonlp-data-bert-covid
co2_eq_emissions: 10.719439124704492
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 407910467
- CO2 Emissions (in grams): 10.719439124704492

## Validation Metrics

- Loss: 0.12029844522476196
- Accuracy: 0.9516339869281045
- Precision: 0.9477786438035853
- Recall: 0.9650793650793651
- AUC: 0.9907376734912967
- F1: 0.9563507668108534

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/nurkayevaa/autonlp-bert-covid-407910467
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("nurkayevaa/autonlp-bert-covid-407910467", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("nurkayevaa/autonlp-bert-covid-407910467", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```