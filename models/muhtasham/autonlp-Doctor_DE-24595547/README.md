---
tags: autonlp
language: de
widget:
- text: "I love AutoNLP 🤗"
datasets:
- muhtasham/autonlp-data-Doctor_DE
co2_eq_emissions: 396.5529429198159
---

# Model Trained Using AutoNLP

- Problem type: Single Column Regression
- Model ID: 24595547
- CO2 Emissions (in grams): 396.5529429198159

## Validation Metrics

- Loss: 1.9565489292144775
- MSE: 1.9565489292144775
- MAE: 0.9890901446342468
- R2: -7.68965036332947e-05
- RMSE: 1.3987668752670288
- Explained Variance: 0.0

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/muhtasham/autonlp-Doctor_DE-24595547
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("muhtasham/autonlp-Doctor_DE-24595547", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("muhtasham/autonlp-Doctor_DE-24595547", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```