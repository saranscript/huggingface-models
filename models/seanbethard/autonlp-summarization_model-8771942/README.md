---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- seanbethard/autonlp-data-summarization_model
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 8771942

## Validation Metrics

- Loss: 0.7463301420211792
- Rouge1: 19.9454
- Rouge2: 13.0362
- RougeL: 17.5797
- RougeLsum: 17.7459
- Gen Len: 19.0

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/seanbethard/autonlp-summarization_model-8771942
```