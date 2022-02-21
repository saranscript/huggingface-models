---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- juliensimon/autonlp-data-imdb-demo-hf
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 16622767

## Validation Metrics

- Loss: 0.20029613375663757
- Accuracy: 0.9256
- Precision: 0.9090909090909091
- Recall: 0.9466984884645983
- AUC: 0.979257749523025
- F1: 0.9275136399064692

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/juliensimon/autonlp-imdb-demo-hf-16622767
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("juliensimon/autonlp-imdb-demo-hf-16622767", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("juliensimon/autonlp-imdb-demo-hf-16622767", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```