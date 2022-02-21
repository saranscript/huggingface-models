---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- arjun3816/autonlp-data-sam_summarization1
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 15492651

## Validation Metrics

- Loss: 1.4060134887695312
- Rouge1: 50.9953
- Rouge2: 35.9204
- RougeL: 43.5673
- RougeLsum: 46.445
- Gen Len: 58.0193

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/arjun3816/autonlp-sam_summarization1-15492651
```