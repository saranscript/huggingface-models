---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- mohsenalam/autonlp-data-billsum-summarization
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 5691253

## Validation Metrics

- Loss: 1.4430530071258545
- Rouge1: 23.9565
- Rouge2: 19.1897
- RougeL: 23.1191
- RougeLsum: 23.3308
- Gen Len: 20.0

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/mohsenalam/autonlp-billsum-summarization-5691253
```