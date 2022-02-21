---
tags: autonlp
language: es
widget:
- text: "I love AutoNLP 🤗"
datasets:
- hiiamsid/autonlp-data-Summarization
co2_eq_emissions: 1133.9679082840014
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 20684328
- CO2 Emissions (in grams): 1133.9679082840014

## Validation Metrics

- Loss: nan
- Rouge1: 9.4193
- Rouge2: 0.91
- RougeL: 7.9376
- RougeLsum: 8.0076
- Gen Len: 10.65

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/hiiamsid/autonlp-Summarization-20684328
```