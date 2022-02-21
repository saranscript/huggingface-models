---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- mmcquade11/autonlp-data-imdb-test
co2_eq_emissions: 298.7849611952843
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 21134442
- CO2 Emissions (in grams): 298.7849611952843

## Validation Metrics

- Loss: 0.21618066728115082
- Accuracy: 0.9393
- Precision: 0.9360730593607306
- Recall: 0.943
- AUC: 0.98362804
- F1: 0.9395237620803029

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/mmcquade11/autonlp-imdb-test-21134442
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("mmcquade11/autonlp-imdb-test-21134442", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("mmcquade11/autonlp-imdb-test-21134442", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```