---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- staceythompson/autonlp-data-myclassification-fortext
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 16332728

## Validation Metrics

- Loss: 0.08077391237020493
- Accuracy: 0.9846153846153847
- Macro F1: 0.9900793650793651
- Micro F1: 0.9846153846153847
- Weighted F1: 0.9846153846153847
- Macro Precision: 0.9900793650793651
- Micro Precision: 0.9846153846153847
- Weighted Precision: 0.9846153846153847
- Macro Recall: 0.9900793650793651
- Micro Recall: 0.9846153846153847
- Weighted Recall: 0.9846153846153847


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/staceythompson/autonlp-myclassification-fortext-16332728
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("staceythompson/autonlp-myclassification-fortext-16332728", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("staceythompson/autonlp-myclassification-fortext-16332728", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```