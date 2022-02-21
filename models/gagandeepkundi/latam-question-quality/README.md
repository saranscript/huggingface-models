---
tags: autonlp
language: es
widget:
- text: "I love AutoNLP 🤗"
datasets:
- gagandeepkundi/autonlp-data-text-classification
co2_eq_emissions: 20.790169878009916
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 19984005
- CO2 Emissions (in grams): 20.790169878009916

## Validation Metrics

- Loss: 0.06693269312381744
- Accuracy: 0.9789
- Precision: 0.9843244336569579
- Recall: 0.9733
- AUC: 0.99695552
- F1: 0.9787811745776348

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/gagandeepkundi/autonlp-text-classification-19984005
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("gagandeepkundi/autonlp-text-classification-19984005", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("gagandeepkundi/autonlp-text-classification-19984005", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```