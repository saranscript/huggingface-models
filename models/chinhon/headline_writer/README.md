---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- chinhon/autonlp-data-sg_headline_generator
co2_eq_emissions: 114.71292762345828
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 25965855
- CO2 Emissions (in grams): 114.71292762345828

## Validation Metrics

- Loss: 1.3862273693084717
- Rouge1: 52.4988
- Rouge2: 31.6973
- RougeL: 47.1727
- RougeLsum: 47.1576
- Gen Len: 17.6194

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/chinhon/autonlp-sg_headline_generator-25965855
```