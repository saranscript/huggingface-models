---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- yosemite/autonlp-data-imdb-sentiment-analysis-english
co2_eq_emissions: 256.38650494338367
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 470512388
- CO2 Emissions (in grams): 256.38650494338367

## Validation Metrics

- Loss: 0.18712733685970306
- Accuracy: 0.9388
- Precision: 0.9300274402195218
- Recall: 0.949
- AUC: 0.98323192
- F1: 0.9394179370421698

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/yosemite/autonlp-imdb-sentiment-analysis-english-470512388
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("yosemite/autonlp-imdb-sentiment-analysis-english-470512388", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("yosemite/autonlp-imdb-sentiment-analysis-english-470512388", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```