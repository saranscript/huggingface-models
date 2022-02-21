---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- dtam/autonlp-data-covid-fake-news
co2_eq_emissions: 123.79523392848652
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 36839110
- CO2 Emissions (in grams): 123.79523392848652

## Validation Metrics

- Loss: 0.17188367247581482
- Accuracy: 0.9714953271028037
- Precision: 0.9917948717948718
- Recall: 0.9480392156862745
- AUC: 0.9947452731092438
- F1: 0.9694235588972432

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/dtam/autonlp-covid-fake-news-36839110
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("dtam/autonlp-covid-fake-news-36839110", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("dtam/autonlp-covid-fake-news-36839110", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```