---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- Jush/autonlp-data-bp
co2_eq_emissions: 3.273303707756322
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 29016523
- CO2 Emissions (in grams): 3.273303707756322

## Validation Metrics

- Loss: 0.6093757748603821
- Accuracy: 0.8333333333333334
- Macro F1: 0.7937936978656889
- Micro F1: 0.8333333333333334
- Weighted F1: 0.8239843785760546
- Macro Precision: 0.8988882462566673
- Micro Precision: 0.8333333333333334
- Weighted Precision: 0.8404982541824647
- Macro Recall: 0.7805142534864643
- Micro Recall: 0.8333333333333334
- Weighted Recall: 0.8333333333333334


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/Jush/autonlp-bp-29016523
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("Jush/autonlp-bp-29016523", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("Jush/autonlp-bp-29016523", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```