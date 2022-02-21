---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- emekaboris/autonlp-data-txc
co2_eq_emissions: 610.861733873082
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 17923129
- CO2 Emissions (in grams): 610.861733873082

## Validation Metrics

- Loss: 0.2319454699754715
- Accuracy: 0.9264228741381642
- Macro F1: 0.6730537318152493
- Micro F1: 0.9264228741381642
- Weighted F1: 0.9251493598895151
- Macro Precision: 0.7767479491141245
- Micro Precision: 0.9264228741381642
- Weighted Precision: 0.9277971545757154
- Macro Recall: 0.6617262519071917
- Micro Recall: 0.9264228741381642
- Weighted Recall: 0.9264228741381642


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/emekaboris/autonlp-txc-17923129
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("emekaboris/autonlp-txc-17923129", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("emekaboris/autonlp-txc-17923129", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```