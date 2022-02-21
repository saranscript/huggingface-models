---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- ds198799/autonlp-data-predict_ROI_1
co2_eq_emissions: 2.7516207978192737
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 29797722
- CO2 Emissions (in grams): 2.7516207978192737

## Validation Metrics

- Loss: 0.6113826036453247
- Accuracy: 0.7559139784946236
- Macro F1: 0.4594734612976928
- Micro F1: 0.7559139784946236
- Weighted F1: 0.7195080232106192
- Macro Precision: 0.7175166413412577
- Micro Precision: 0.7559139784946236
- Weighted Precision: 0.7383048259333735
- Macro Recall: 0.4482203645846237
- Micro Recall: 0.7559139784946236
- Weighted Recall: 0.7559139784946236


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/ds198799/autonlp-predict_ROI_1-29797722
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("ds198799/autonlp-predict_ROI_1-29797722", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("ds198799/autonlp-predict_ROI_1-29797722", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```