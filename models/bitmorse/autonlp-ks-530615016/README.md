---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- bitmorse/autonlp-data-ks
co2_eq_emissions: 2.2247356264808964
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 530615016
- CO2 Emissions (in grams): 2.2247356264808964

## Validation Metrics

- Loss: 0.7859578132629395
- Accuracy: 0.676854818831649
- Macro F1: 0.3297126297995653
- Micro F1: 0.676854818831649
- Weighted F1: 0.6429522696884535
- Macro Precision: 0.33152557743856437
- Micro Precision: 0.676854818831649
- Weighted Precision: 0.6276125515413322
- Macro Recall: 0.33784302289888885
- Micro Recall: 0.676854818831649
- Weighted Recall: 0.676854818831649


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/bitmorse/autonlp-ks-530615016
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("bitmorse/autonlp-ks-530615016", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("bitmorse/autonlp-ks-530615016", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```