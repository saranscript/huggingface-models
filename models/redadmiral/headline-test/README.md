---
tags: autonlp
language: de
widget:
- text: "I love AutoNLP 🤗"
datasets:
- redadmiral/autonlp-data-Headline-Generator
co2_eq_emissions: 651.3545590912366
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 453611714
- CO2 Emissions (in grams): 651.3545590912366

## Validation Metrics

- Loss: nan
- Rouge1: 2.8187
- Rouge2: 0.5508
- RougeL: 2.7396
- RougeLsum: 2.7446
- Gen Len: 9.7507

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/redadmiral/autonlp-Headline-Generator-453611714
```