---
tags: autonlp
language: ko
widget:
- text: "I love AutoNLP 🤗"
datasets:
- ybybybybybybyb/autonlp-data-revanalysis
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 6711455

## Validation Metrics

- Loss: 0.8241586089134216
- Accuracy: 0.7835820895522388
- Macro F1: 0.5297383029341792
- Micro F1: 0.783582089552239
- Weighted F1: 0.7130091019920225
- Macro Precision: 0.48787061994609165
- Micro Precision: 0.7835820895522388
- Weighted Precision: 0.6541416904694856
- Macro Recall: 0.5795454545454546
- Micro Recall: 0.7835820895522388
- Weighted Recall: 0.7835820895522388


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/ybybybybybybyb/autonlp-revanalysis-6711455
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ybybybybybybyb/autonlp-revanalysis-6711455", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("ybybybybybybyb/autonlp-revanalysis-6711455", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```