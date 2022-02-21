---
tags: autonlp
language: hi
widget:
- text: "I love AutoNLP 🤗"
datasets:
- rohansingh/autonlp-data-Fake-news-detection-system
co2_eq_emissions: 3.8624397961432106
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 29906863
- CO2 Emissions (in grams): 3.8624397961432106

## Validation Metrics

- Loss: 0.2536192238330841
- Accuracy: 0.9084807809640024
- Precision: 0.9421172886519421
- Recall: 0.9435545385202135
- AUC: 0.9517288050454876
- F1: 0.9428353658536586

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/rohansingh/autonlp-Fake-news-detection-system-29906863
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("rohansingh/autonlp-Fake-news-detection-system-29906863", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("rohansingh/autonlp-Fake-news-detection-system-29906863", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```