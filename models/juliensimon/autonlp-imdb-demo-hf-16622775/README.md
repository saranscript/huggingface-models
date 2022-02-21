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
- Model ID: 16622775

## Validation Metrics

- Loss: 0.18653589487075806
- Accuracy: 0.9408
- Precision: 0.9537643207855974
- Recall: 0.9272076372315036
- AUC: 0.985847396174344
- F1: 0.9402985074626865

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/juliensimon/autonlp-imdb-demo-hf-16622775
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("juliensimon/autonlp-imdb-demo-hf-16622775", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("juliensimon/autonlp-imdb-demo-hf-16622775", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```