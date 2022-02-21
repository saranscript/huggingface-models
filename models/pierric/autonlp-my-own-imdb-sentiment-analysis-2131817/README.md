---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- pierric/autonlp-data-my-own-imdb-sentiment-analysis
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 2131817

## Validation Metrics

- Loss: 0.24430708587169647
- Accuracy: 0.9452
- Precision: 0.9303944315545244
- Recall: 0.9624
- AUC: 0.9793824287999999
- F1: 0.946126622099882

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/pierric/autonlp-my-own-imdb-sentiment-analysis-2131817
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("pierric/autonlp-my-own-imdb-sentiment-analysis-2131817", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("pierric/autonlp-my-own-imdb-sentiment-analysis-2131817", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```