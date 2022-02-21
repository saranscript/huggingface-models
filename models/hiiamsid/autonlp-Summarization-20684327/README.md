---
tags: autonlp
language: es
widget:
- text: "I love AutoNLP 🤗"
datasets:
- hiiamsid/autonlp-data-Summarization
co2_eq_emissions: 437.2441955971972
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 20684327
- CO2 Emissions (in grams): 437.2441955971972

## Validation Metrics

- Loss: nan
- Rouge1: 3.7729
- Rouge2: 0.4152
- RougeL: 3.5066
- RougeLsum: 3.5167
- Gen Len: 5.0577

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/hiiamsid/autonlp-Summarization-20684327
```