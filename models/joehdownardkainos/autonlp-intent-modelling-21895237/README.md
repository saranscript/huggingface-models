---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- joehdownardkainos/autonlp-data-intent-modelling
co2_eq_emissions: 1.5688902203257171
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 21895237
- CO2 Emissions (in grams): 1.5688902203257171

## Validation Metrics

- Loss: 1.6614878177642822
- Rouge1: 32.4158
- Rouge2: 24.6194
- RougeL: 29.9278
- RougeLsum: 29.4988
- Gen Len: 58.7778

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/joehdownardkainos/autonlp-intent-modelling-21895237
```