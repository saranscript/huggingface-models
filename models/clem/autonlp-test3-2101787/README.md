---
tags: autonlp
language: en
widget:
- text: "this can wait"
datasets:
- clem/autonlp-data-test3
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification Urgent/Not Urgent

## Validation Metrics

- Loss: 0.08956164121627808
- Accuracy: 1.0
- Precision: 1.0
- Recall: 1.0
- AUC: 1.0
- F1: 1.0

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/clem/autonlp-test3-2101787
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("clem/autonlp-test3-2101787", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("clem/autonlp-test3-2101787", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```