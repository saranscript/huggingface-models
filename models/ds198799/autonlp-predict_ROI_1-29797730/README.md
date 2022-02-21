---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- ds198799/autonlp-data-predict_ROI_1
co2_eq_emissions: 2.2439127664461718
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 29797730
- CO2 Emissions (in grams): 2.2439127664461718

## Validation Metrics

- Loss: 0.6314184069633484
- Accuracy: 0.7596774193548387
- Macro F1: 0.4740565300039588
- Micro F1: 0.7596774193548386
- Weighted F1: 0.7371623804622154
- Macro Precision: 0.6747804619412134
- Micro Precision: 0.7596774193548387
- Weighted Precision: 0.7496542175358931
- Macro Recall: 0.47743727441146655
- Micro Recall: 0.7596774193548387
- Weighted Recall: 0.7596774193548387


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/ds198799/autonlp-predict_ROI_1-29797730
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ds198799/autonlp-predict_ROI_1-29797730", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("ds198799/autonlp-predict_ROI_1-29797730", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```