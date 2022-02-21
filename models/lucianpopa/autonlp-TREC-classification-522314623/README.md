---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- lucianpopa/autonlp-data-TREC-classification
co2_eq_emissions: 15.186006626915715
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 522314623
- CO2 Emissions (in grams): 15.186006626915715

## Validation Metrics

- Loss: 0.24612033367156982
- Accuracy: 0.9643183897529735
- Macro F1: 0.9493690949638435
- Micro F1: 0.9643183897529735
- Weighted F1: 0.9642384162837268
- Macro Precision: 0.9372705571897225
- Micro Precision: 0.9643183897529735
- Weighted Precision: 0.9652870438320825
- Macro Recall: 0.9649638583139503
- Micro Recall: 0.9643183897529735
- Weighted Recall: 0.9643183897529735


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/lucianpopa/autonlp-TREC-classification-522314623
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("lucianpopa/autonlp-TREC-classification-522314623", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("lucianpopa/autonlp-TREC-classification-522314623", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```