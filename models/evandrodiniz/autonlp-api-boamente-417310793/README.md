---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- evandrodiniz/autonlp-data-api-boamente
co2_eq_emissions: 9.446754273734577
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 417310793
- CO2 Emissions (in grams): 9.446754273734577

## Validation Metrics

- Loss: 0.25755178928375244
- Accuracy: 0.9407114624505929
- Precision: 0.8600823045267489
- Recall: 0.95
- AUC: 0.9732501264968797
- F1: 0.9028077753779697

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/evandrodiniz/autonlp-api-boamente-417310793
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("evandrodiniz/autonlp-api-boamente-417310793", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("evandrodiniz/autonlp-api-boamente-417310793", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```