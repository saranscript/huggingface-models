---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- idjotherwise/autonlp-data-reading_prediction
---

# Model Trained Using AutoNLP

- Problem type: Single Column Regression
- Model ID: 172506

## Validation Metrics

- Loss: 0.03257797285914421
- MSE: 0.03257797285914421
- MAE: 0.14246532320976257
- R2: 0.9693824457290849
- RMSE: 0.18049369752407074
- Explained Variance: 0.9699198007583618

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/idjotherwise/autonlp-reading_prediction-172506
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("idjotherwise/autonlp-reading_prediction-172506")

tokenizer = AutoTokenizer.from_pretrained("idjotherwise/autonlp-reading_prediction-172506")

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```