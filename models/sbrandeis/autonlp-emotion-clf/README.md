---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- sbrandeis/autonlp-data-emotion-classification-pre
co2_eq_emissions: 23.4692320403666
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 3252433
- CO2 Emissions (in grams): 23.4692320403666

## Validation Metrics

- Loss: 0.15040820837020874
- Accuracy: 0.9438026849828286
- Macro F1: 0.9093924156122387
- Micro F1: 0.9438026849828286
- Weighted F1: 0.9423168992167734
- Macro Precision: 0.9482796335288181
- Micro Precision: 0.9438026849828286
- Weighted Precision: 0.9466095426853992
- Macro Recall: 0.8842649120281764
- Micro Recall: 0.9438026849828286
- Weighted Recall: 0.9438026849828286


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/sbrandeis/autonlp-emotion-classification-pre-3252433
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("sbrandeis/autonlp-emotion-classification-pre-3252433", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("sbrandeis/autonlp-emotion-classification-pre-3252433", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```
