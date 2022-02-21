---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- divyshah/autonlp-data-text-categorization
co2_eq_emissions: 214.76275947482927
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 38039618
- CO2 Emissions (in grams): 214.76275947482927

## Validation Metrics

- Loss: 0.791480541229248
- Accuracy: 0.7748376232860236
- Macro F1: 0.531348420438711
- Micro F1: 0.7748376232860236
- Weighted F1: 0.7677422775303853
- Macro Precision: 0.5683205175316921
- Micro Precision: 0.7748376232860236
- Weighted Precision: 0.7712212956179081
- Macro Recall: 0.5245470037653356
- Micro Recall: 0.7748376232860236
- Weighted Recall: 0.7748376232860236


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/divyshah/autonlp-text-categorization-38039618
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("divyshah/autonlp-text-categorization-38039618", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("divyshah/autonlp-text-categorization-38039618", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```