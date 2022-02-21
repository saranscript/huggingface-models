---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- Anorak/autonlp-data-Niravana-test2
co2_eq_emissions: 4.214012748213151
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 20384195
- CO2 Emissions (in grams): 4.214012748213151

## Validation Metrics

- Loss: 1.0120062828063965
- Rouge1: 41.1808
- Rouge2: 26.2564
- RougeL: 31.3106
- RougeLsum: 38.9991
- Gen Len: 58.45

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/Anorak/autonlp-Niravana-test2-20384195
```