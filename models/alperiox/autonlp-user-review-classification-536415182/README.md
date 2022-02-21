---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- alperiox/autonlp-data-user-review-classification
co2_eq_emissions: 1.268309634217171
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 536415182
- CO2 Emissions (in grams): 1.268309634217171

## Validation Metrics

- Loss: 0.44733062386512756
- Accuracy: 0.8873239436619719
- Macro F1: 0.8859416445623343
- Micro F1: 0.8873239436619719
- Weighted F1: 0.8864646766540891
- Macro Precision: 0.8848522167487685
- Micro Precision: 0.8873239436619719
- Weighted Precision: 0.8883299798792756
- Macro Recall: 0.8908045977011494
- Micro Recall: 0.8873239436619719
- Weighted Recall: 0.8873239436619719


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/alperiox/autonlp-user-review-classification-536415182
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("alperiox/autonlp-user-review-classification-536415182", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("alperiox/autonlp-user-review-classification-536415182", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```