---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- juliensimon/autonlp-data-reuters-summarization
co2_eq_emissions: 206.46626351359515
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 31447312
- CO2 Emissions (in grams): 206.46626351359515

## Validation Metrics

- Loss: 1.1907752752304077
- Rouge1: 55.9215
- Rouge2: 30.7724
- RougeL: 53.185
- RougeLsum: 53.3353
- Gen Len: 15.1236

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/juliensimon/autonlp-reuters-summarization-31447312
```