---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- bshlgrs/autonlp-data-classification
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 9522090

## Validation Metrics

- Loss: 0.3541755676269531
- Accuracy: 0.8759671179883946
- Macro F1: 0.5330133182738012
- Micro F1: 0.8759671179883946
- Weighted F1: 0.8482773065757196
- Macro Precision: 0.537738108882869
- Micro Precision: 0.8759671179883946
- Weighted Precision: 0.8241048710814852
- Macro Recall: 0.5316621214820499
- Micro Recall: 0.8759671179883946
- Weighted Recall: 0.8759671179883946


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/bshlgrs/autonlp-classification-9522090
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("bshlgrs/autonlp-classification-9522090", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("bshlgrs/autonlp-classification-9522090", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```