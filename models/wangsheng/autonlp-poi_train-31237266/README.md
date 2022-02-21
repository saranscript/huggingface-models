---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- wangsheng/autonlp-data-poi_train
co2_eq_emissions: 390.39411176775826
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 31237266
- CO2 Emissions (in grams): 390.39411176775826

## Validation Metrics

- Loss: 0.1643059253692627
- Accuracy: 0.9379398019660155
- Precision: 0.7467491278147795
- Recall: 0.7158710854363028
- AUC: 0.9631629384458238
- F1: 0.7309841664079478

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/wangsheng/autonlp-poi_train-31237266
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("wangsheng/autonlp-poi_train-31237266", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("wangsheng/autonlp-poi_train-31237266", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```