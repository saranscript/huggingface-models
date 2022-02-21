---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- staceythompson/autonlp-data-new-text-classification
co2_eq_emissions: 2.0318857468309206
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 38319698
- CO2 Emissions (in grams): 2.0318857468309206

## Validation Metrics

- Loss: 0.04461582377552986
- Accuracy: 0.9909255898366606
- Macro F1: 0.9951842095089771
- Micro F1: 0.9909255898366606
- Weighted F1: 0.9909493945587176
- Macro Precision: 0.9942196531791907
- Micro Precision: 0.9909255898366606
- Weighted Precision: 0.9911878560263526
- Macro Recall: 0.9962686567164181
- Micro Recall: 0.9909255898366606
- Weighted Recall: 0.9909255898366606


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/staceythompson/autonlp-new-text-classification-38319698
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("staceythompson/autonlp-new-text-classification-38319698", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("staceythompson/autonlp-new-text-classification-38319698", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```