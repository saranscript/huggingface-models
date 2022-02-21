---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- chinhon/autonlp-data-sg_headline_generator
co2_eq_emissions: 396.629376395644
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 25965856
- CO2 Emissions (in grams): 396.629376395644

## Validation Metrics

- Loss: 1.4130597114562988
- Rouge1: 51.7922
- Rouge2: 30.8259
- RougeL: 46.4585
- RougeLsum: 46.4807
- Gen Len: 15.8411

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/chinhon/autonlp-sg_headline_generator-25965856
```