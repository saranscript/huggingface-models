---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- kamivao/autonlp-data-cola_gram
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 208681

## Validation Metrics

- Loss: 0.37569838762283325
- Accuracy: 0.8365019011406845
- Precision: 0.8398058252427184
- Recall: 0.9453551912568307
- AUC: 0.9048838797814208
- F1: 0.8894601542416453

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/kamivao/autonlp-cola_gram-208681
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("kamivao/autonlp-cola_gram-208681", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("kamivao/autonlp-cola_gram-208681", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```