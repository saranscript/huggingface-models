---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- imzachjohnson/autonlp-data-spinner-check
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 16492731

## Validation Metrics

- Loss: 0.21610039472579956
- Accuracy: 0.9155366722657816
- Precision: 0.9530714194995978
- Recall: 0.944871149164778
- AUC: 0.9553238723676906
- F1: 0.9489535692456846

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/imzachjohnson/autonlp-spinner-check-16492731
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("imzachjohnson/autonlp-spinner-check-16492731", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("imzachjohnson/autonlp-spinner-check-16492731", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```