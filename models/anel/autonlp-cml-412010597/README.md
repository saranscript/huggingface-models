---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- anel/autonlp-data-cml
co2_eq_emissions: 10.411685187181709
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 412010597
- CO2 Emissions (in grams): 10.411685187181709

## Validation Metrics

- Loss: 0.12585781514644623
- Accuracy: 0.9475446428571429
- Precision: 0.9454660748256183
- Recall: 0.964424320827943
- AUC: 0.990229573862156
- F1: 0.9548511047070125

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/anel/autonlp-cml-412010597
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("anel/autonlp-cml-412010597", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("anel/autonlp-cml-412010597", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```