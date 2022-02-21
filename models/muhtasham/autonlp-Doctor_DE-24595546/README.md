---
tags: autonlp
language: de
widget:
- text: "I love AutoNLP 🤗"
datasets:
- muhtasham/autonlp-data-Doctor_DE
co2_eq_emissions: 210.5957437893554
---

# Model Trained Using AutoNLP

- Problem type: Single Column Regression
- Model ID: 24595546
- CO2 Emissions (in grams): 210.5957437893554

## Validation Metrics

- Loss: 0.3092539310455322
- MSE: 0.30925390124320984
- MAE: 0.25015318393707275
- R2: 0.841926941198094
- RMSE: 0.5561060309410095
- Explained Variance: 0.8427215218544006

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/muhtasham/autonlp-Doctor_DE-24595546
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("muhtasham/autonlp-Doctor_DE-24595546", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("muhtasham/autonlp-Doctor_DE-24595546", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```