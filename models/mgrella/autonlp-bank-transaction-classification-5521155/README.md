---
tags: autonlp
language: it
widget:
- text: "I love AutoNLP 🤗"
datasets:
- mgrella/autonlp-data-bank-transaction-classification
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 5521155

## Validation Metrics

- Loss: 1.3173143863677979
- Accuracy: 0.8220706757594545
- Macro F1: 0.5713688384455807
- Micro F1: 0.8220706757594544
- Weighted F1: 0.8217158913702755
- Macro Precision: 0.6064387992817253
- Micro Precision: 0.8220706757594545
- Weighted Precision: 0.8491515834140735
- Macro Recall: 0.5873349311175117
- Micro Recall: 0.8220706757594545
- Weighted Recall: 0.8220706757594545


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/mgrella/autonlp-bank-transaction-classification-5521155
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("mgrella/autonlp-bank-transaction-classification-5521155", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("mgrella/autonlp-bank-transaction-classification-5521155", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```