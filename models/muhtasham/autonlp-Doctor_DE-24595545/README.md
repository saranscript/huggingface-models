---
tags: autonlp
language: de
widget:
- text: "I love AutoNLP 🤗"
datasets:
- muhtasham/autonlp-data-Doctor_DE
co2_eq_emissions: 203.30658367993382
---

# Model Trained Using AutoNLP

- Problem type: Single Column Regression
- Model ID: 24595545
- CO2 Emissions (in grams): 203.30658367993382

## Validation Metrics

- Loss: 0.30214861035346985
- MSE: 0.30214861035346985
- MAE: 0.25911855697631836
- R2: 0.8455587614373526
- RMSE: 0.5496804714202881
- Explained Variance: 0.8476610779762268

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/muhtasham/autonlp-Doctor_DE-24595545
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("muhtasham/autonlp-Doctor_DE-24595545", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("muhtasham/autonlp-Doctor_DE-24595545", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```