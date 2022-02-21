---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- sam890914/autonlp-data-roberta-large2
co2_eq_emissions: 71.60954851696604
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 479012819
- CO2 Emissions (in grams): 71.60954851696604

## Validation Metrics

- Loss: 0.22774338722229004
- Accuracy: 0.9395126938149599
- Precision: 0.9677075940383251
- Recall: 0.9117352056168505
- AUC: 0.9862377263827619
- F1: 0.9388879325185058

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/sam890914/autonlp-roberta-large2-479012819
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("sam890914/autonlp-roberta-large2-479012819", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("sam890914/autonlp-roberta-large2-479012819", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```