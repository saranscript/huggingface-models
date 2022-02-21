---
tags: autonlp
language: fr
widget:
- text: "I love AutoNLP 🤗"
datasets:
- pierreant-p/autonlp-data-jcvd-or-linkedin
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 3471039

## Validation Metrics

- Loss: 0.6704344749450684
- Accuracy: 0.59375
- Macro F1: 0.37254901960784315
- Micro F1: 0.59375
- Weighted F1: 0.4424019607843137
- Macro Precision: 0.296875
- Micro Precision: 0.59375
- Weighted Precision: 0.3525390625
- Macro Recall: 0.5
- Micro Recall: 0.59375
- Weighted Recall: 0.59375


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/pierreant-p/autonlp-jcvd-or-linkedin-3471039
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("pierreant-p/autonlp-jcvd-or-linkedin-3471039", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("pierreant-p/autonlp-jcvd-or-linkedin-3471039", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```