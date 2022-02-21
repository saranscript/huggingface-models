---
tags: autonlp
language: de
widget:
- text: "I love AutoNLP 🤗"
datasets:
- muhtasham/autonlp-data-Doctor_DE
co2_eq_emissions: 183.88911013564527
---

# Model Trained Using AutoNLP

- Problem type: Single Column Regression
- Model ID: 24595548
- CO2 Emissions (in grams): 183.88911013564527

## Validation Metrics

- Loss: 0.3050823509693146
- MSE: 0.3050823509693146
- MAE: 0.2664000689983368
- R2: 0.844059188176304
- RMSE: 0.5523425936698914
- Explained Variance: 0.8472161293029785

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/muhtasham/autonlp-Doctor_DE-24595548
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("muhtasham/autonlp-Doctor_DE-24595548", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("muhtasham/autonlp-Doctor_DE-24595548", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```