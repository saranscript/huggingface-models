---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- gborn/autonlp-data-news-summarization
co2_eq_emissions: 210.6348731063569
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 483413089
- CO2 Emissions (in grams): 210.6348731063569

## Validation Metrics

- Loss: 1.8478657007217407
- Rouge1: 50.5981
- Rouge2: 26.2167
- RougeL: 46.0513
- RougeLsum: 46.061
- Gen Len: 13.5987

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/gborn/autonlp-news-summarization-483413089
```