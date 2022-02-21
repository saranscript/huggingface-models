---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- dee4hf/autonlp-data-shajBERT
co2_eq_emissions: 11.98841452241473
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 38639804
- CO2 Emissions (in grams): 11.98841452241473

## Validation Metrics

- Loss: 0.421400249004364
- Accuracy: 0.86783988957902
- Macro F1: 0.8669477050676501
- Micro F1: 0.86783988957902
- Weighted F1: 0.86694770506765
- Macro Precision: 0.867606300132228
- Micro Precision: 0.86783988957902
- Weighted Precision: 0.8676063001322278
- Macro Recall: 0.86783988957902
- Micro Recall: 0.86783988957902
- Weighted Recall: 0.86783988957902


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/dee4hf/autonlp-shajBERT-38639804
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("dee4hf/autonlp-shajBERT-38639804", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("dee4hf/autonlp-shajBERT-38639804", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```