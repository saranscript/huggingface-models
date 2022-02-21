---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- arjun3816/autonlp-data-pegas_large_samsum
---

# Model Trained Using AutoNLP

- Problem type: Summarization
- Model ID: 15892673

## Validation Metrics

- Loss: 1.3661842346191406
- Rouge1: 50.8868
- Rouge2: 26.996
- RougeL: 42.9088
- RougeLsum: 46.6748
- Gen Len: 20.716

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_HUGGINGFACE_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/arjun3816/autonlp-pegas_large_samsum-15892673
```