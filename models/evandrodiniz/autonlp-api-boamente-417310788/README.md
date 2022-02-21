---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- evandrodiniz/autonlp-data-api-boamente
co2_eq_emissions: 6.826886567147602
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 417310788
- CO2 Emissions (in grams): 6.826886567147602

## Validation Metrics

- Loss: 0.20949310064315796
- Accuracy: 0.9578392621870883
- Precision: 0.9476190476190476
- Recall: 0.9045454545454545
- AUC: 0.9714032720526227
- F1: 0.9255813953488372

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/evandrodiniz/autonlp-api-boamente-417310788
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("evandrodiniz/autonlp-api-boamente-417310788", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("evandrodiniz/autonlp-api-boamente-417310788", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```