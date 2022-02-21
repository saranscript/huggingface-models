---
tags: autonlp
language: nl
widget:
- text: "I love AutoNLP 🤗"
datasets:
- maximedb/autonlp-data-vaccinchat
co2_eq_emissions: 14.525955245648218
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 22134694
- CO2 Emissions (in grams): 14.525955245648218

## Validation Metrics

- Loss: 1.7039562463760376
- Accuracy: 0.6369376479873717
- Macro F1: 0.5363181342408181
- Micro F1: 0.6369376479873717
- Weighted F1: 0.6309793486221543
- Macro Precision: 0.5533353910494714
- Micro Precision: 0.6369376479873717
- Weighted Precision: 0.676981050732216
- Macro Recall: 0.5828723356986293
- Micro Recall: 0.6369376479873717
- Weighted Recall: 0.6369376479873717


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/maximedb/autonlp-vaccinchat-22134694
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("maximedb/autonlp-vaccinchat-22134694", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("maximedb/autonlp-vaccinchat-22134694", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```