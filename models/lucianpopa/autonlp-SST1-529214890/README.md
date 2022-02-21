---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- lucianpopa/autonlp-data-SST1
co2_eq_emissions: 49.618294309910624
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 529214890
- CO2 Emissions (in grams): 49.618294309910624

## Validation Metrics

- Loss: 0.7135734558105469
- Accuracy: 0.7042338838232481
- Macro F1: 0.6164041045783032
- Micro F1: 0.7042338838232481
- Weighted F1: 0.7028309161791009
- Macro Precision: 0.6497438111060598
- Micro Precision: 0.7042338838232481
- Weighted Precision: 0.7076651075198755
- Macro Recall: 0.6023419083862918
- Micro Recall: 0.7042338838232481
- Weighted Recall: 0.7042338838232481


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/lucianpopa/autonlp-SST1-529214890
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("lucianpopa/autonlp-SST1-529214890", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("lucianpopa/autonlp-SST1-529214890", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```