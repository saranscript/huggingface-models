---
tags: autonlp
language: de
widget:
- text: "I love AutoNLP 🤗"
datasets:
- muhtasham/autonlp-data-Doctor_DE
co2_eq_emissions: 92.87363201770962
---

# Model Trained Using AutoNLP

- Problem type: Single Column Regression
- Model ID: 24595544
- CO2 Emissions (in grams): 92.87363201770962

## Validation Metrics

- Loss: 0.3001164197921753
- MSE: 0.3001164197921753
- MAE: 0.24272102117538452
- R2: 0.8465975006681247
- RMSE: 0.5478288531303406
- Explained Variance: 0.8468209505081177

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/muhtasham/autonlp-Doctor_DE-24595544
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("muhtasham/autonlp-Doctor_DE-24595544", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("muhtasham/autonlp-Doctor_DE-24595544", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```