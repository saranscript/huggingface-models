---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- am4nsolanki/autonlp-data-text-hateful-memes
co2_eq_emissions: 1.4280361775467445
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 36789092
- CO2 Emissions (in grams): 1.4280361775467445

## Validation Metrics

- Loss: 0.5255328416824341
- Accuracy: 0.7666078777189889
- Precision: 0.6913123844731978
- Recall: 0.6192052980132451
- AUC: 0.7893359070795125
- F1: 0.6532751091703057

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/am4nsolanki/autonlp-text-hateful-memes-36789092
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("am4nsolanki/autonlp-text-hateful-memes-36789092", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("am4nsolanki/autonlp-text-hateful-memes-36789092", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```