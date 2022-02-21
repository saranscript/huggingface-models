---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- mmcquade11/autonlp-data-imdb-test
co2_eq_emissions: 38.102565360610484
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 21134453
- CO2 Emissions (in grams): 38.102565360610484

## Validation Metrics

- Loss: 0.172550767660141
- Accuracy: 0.9355
- Precision: 0.9362853135644159
- Recall: 0.9346
- AUC: 0.98267064
- F1: 0.9354418977079372

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/mmcquade11/autonlp-imdb-test-21134453
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("mmcquade11/autonlp-imdb-test-21134453", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("mmcquade11/autonlp-imdb-test-21134453", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```