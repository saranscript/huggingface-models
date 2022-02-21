---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- danicodes/autonlp-data-legal-text-summary
co2_eq_emissions: 10.148805588432941
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 457311749
- CO2 Emissions (in grams): 10.148805588432941

## Validation Metrics

- Loss: 1.647747278213501
- Rouge1: 32.4854
- Rouge2: 19.8974
- RougeL: 30.0602
- RougeLsum: 29.9377
- Gen Len: 46.6556

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/danicodes/autonlp-legal-text-summary-457311749
```