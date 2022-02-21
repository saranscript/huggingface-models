---
tags: autonlp
language: zh
widget:
- text: "I love AutoNLP 🤗"
datasets:
- ysslang/autonlp-data-test
co2_eq_emissions: 10.9230691350863
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 459011902
- CO2 Emissions (in grams): 10.9230691350863

## Validation Metrics

- Loss: 0.7189690470695496
- Accuracy: 0.7453263867606497
- Macro F1: 0.630810193227066
- Micro F1: 0.7453263867606497
- Weighted F1: 0.7399327942874923
- Macro Precision: 0.656237447101913
- Micro Precision: 0.7453263867606497
- Weighted Precision: 0.7410161412822164
- Macro Recall: 0.6340140718425453
- Micro Recall: 0.7453263867606497
- Weighted Recall: 0.7453263867606497


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/ysslang/autonlp-test-459011902
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ysslang/autonlp-test-459011902", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("ysslang/autonlp-test-459011902", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```