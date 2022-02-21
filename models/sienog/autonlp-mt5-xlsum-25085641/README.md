---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- sienog/autonlp-data-mt5-xlsum
co2_eq_emissions: 11.166602089650883
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 25085641
- CO2 Emissions (in grams): 11.166602089650883

## Validation Metrics

- Loss: 1.173471212387085
- Rouge1: 51.7353
- Rouge2: 36.6771
- RougeL: 45.4129
- RougeLsum: 48.8512
- Gen Len: 82.9375

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/sienog/autonlp-mt5-xlsum-25085641
```