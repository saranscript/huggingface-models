---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- lidiia/autonlp-data-trans_class_arg
co2_eq_emissions: 0.9756221672668951
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 32957902
- CO2 Emissions (in grams): 0.9756221672668951

## Validation Metrics

- Loss: 0.2765039801597595
- Accuracy: 0.8939828080229226
- Precision: 0.7757009345794392
- Recall: 0.8645833333333334
- AUC: 0.9552659749670619
- F1: 0.8177339901477833

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/lidiia/autonlp-trans_class_arg-32957902
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("lidiia/autonlp-trans_class_arg-32957902", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("lidiia/autonlp-trans_class_arg-32957902", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```