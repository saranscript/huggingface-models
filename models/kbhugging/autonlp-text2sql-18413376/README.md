---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- kbhugging/autonlp-data-text2sql
co2_eq_emissions: 1.4091714704861447
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 18413376
- CO2 Emissions (in grams): 1.4091714704861447

## Validation Metrics

- Loss: 0.26672711968421936
- Rouge1: 61.765
- Rouge2: 52.5778
- RougeL: 61.3222
- RougeLsum: 61.1905
- Gen Len: 18.7805

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/kbhugging/autonlp-text2sql-18413376
```