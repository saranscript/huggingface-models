---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- testing/autonlp-data-ingredient_sentiment_analysis
co2_eq_emissions: 1.8458289701133035
---

# Model Trained Using AutoNLP

- Problem type: Entity Extraction
- Model ID: 19126711
- CO2 Emissions (in grams): 1.8458289701133035

## Validation Metrics

- Loss: 0.054593171924352646
- Accuracy: 0.9790668170284748
- Precision: 0.8029411764705883
- Recall: 0.6026490066225165
- F1: 0.6885245901639344

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/testing/autonlp-ingredient_sentiment_analysis-19126711
```

Or Python API:

```
from transformers import AutoModelForTokenClassification, AutoTokenizer

model = AutoModelForTokenClassification.from_pretrained("testing/autonlp-ingredient_sentiment_analysis-19126711", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("testing/autonlp-ingredient_sentiment_analysis-19126711", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```