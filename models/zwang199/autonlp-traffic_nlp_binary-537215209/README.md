---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- zwang199/autonlp-data-traffic_nlp_binary
co2_eq_emissions: 1.171798205242445
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 537215209
- CO2 Emissions (in grams): 1.171798205242445

## Validation Metrics

- Loss: 0.3879534602165222
- Accuracy: 0.8597449908925319
- Precision: 0.8318042813455657
- Recall: 0.9251700680272109
- AUC: 0.9230158730158731
- F1: 0.8760064412238325

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/zwang199/autonlp-traffic_nlp_binary-537215209
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("zwang199/autonlp-traffic_nlp_binary-537215209", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("zwang199/autonlp-traffic_nlp_binary-537215209", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```