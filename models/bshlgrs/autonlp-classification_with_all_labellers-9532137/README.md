---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- bshlgrs/autonlp-data-classification_with_all_labellers
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 9532137

## Validation Metrics

- Loss: 0.34556105732917786
- Accuracy: 0.8749890724713699
- Macro F1: 0.5243623959669343
- Micro F1: 0.8749890724713699
- Weighted F1: 0.8638030768409057
- Macro Precision: 0.5016762404900895
- Micro Precision: 0.8749890724713699
- Weighted Precision: 0.8547962562614184
- Macro Recall: 0.5529674694200845
- Micro Recall: 0.8749890724713699
- Weighted Recall: 0.8749890724713699


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/bshlgrs/autonlp-classification_with_all_labellers-9532137
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("bshlgrs/autonlp-classification_with_all_labellers-9532137", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("bshlgrs/autonlp-classification_with_all_labellers-9532137", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```