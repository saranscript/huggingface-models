---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- rexxar96/autonlp-data-sentiment-analysis
co2_eq_emissions: 22.28263989637389
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 456211724
- CO2 Emissions (in grams): 22.28263989637389

## Validation Metrics

- Loss: 0.23710417747497559
- Accuracy: 0.9119100357812234
- Precision: 0.8882611424984307
- Recall: 0.9461718488799733
- AUC: 0.974790366001874
- F1: 0.9163024121741946

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/rexxar96/autonlp-sentiment-analysis-456211724
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("rexxar96/autonlp-sentiment-analysis-456211724", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("rexxar96/autonlp-sentiment-analysis-456211724", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```