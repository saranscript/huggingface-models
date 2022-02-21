---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- m3tafl0ps/autonlp-data-NLPIsFun
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 251844

## Validation Metrics

- Loss: 0.38616305589675903
- Accuracy: 0.8356545961002786
- Precision: 0.8253968253968254
- Recall: 0.8571428571428571
- AUC: 0.9222387781709815
- F1: 0.8409703504043127

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/m3tafl0ps/autonlp-NLPIsFun-251844
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("m3tafl0ps/autonlp-NLPIsFun-251844", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("m3tafl0ps/autonlp-NLPIsFun-251844", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```