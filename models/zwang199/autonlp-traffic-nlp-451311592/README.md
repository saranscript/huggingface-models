---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- zwang199/autonlp-data-traffic-nlp
co2_eq_emissions: 1.8697144296865242
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 451311592
- CO2 Emissions (in grams): 1.8697144296865242

## Validation Metrics

- Loss: 0.4544260799884796
- Accuracy: 0.8042452830188679
- Precision: 0.8331288343558282
- Recall: 0.8573232323232324
- AUC: 0.8759811658249159
- F1: 0.8450528935905414

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/zwang199/autonlp-traffic-nlp-451311592
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("zwang199/autonlp-traffic-nlp-451311592", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("zwang199/autonlp-traffic-nlp-451311592", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```