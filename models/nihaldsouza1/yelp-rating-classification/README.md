---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- nihaldsouza1/autonlp-data-yelp-rating-classification
co2_eq_emissions: 15.62335109262394
---

# Custom-trained user model

- Problem type: Multi-class Classification
- Model ID: 545015430
- CO2 Emissions (in grams): 15.62335109262394

## Validation Metrics

- Loss: 0.7870086431503296
- Accuracy: 0.6631428571428571
- Macro F1: 0.6613073053700258
- Micro F1: 0.6631428571428571
- Weighted F1: 0.661157273964887
- Macro Precision: 0.6626911151999393
- Micro Precision: 0.6631428571428571
- Weighted Precision: 0.662191421927851
- Macro Recall: 0.6629735627465572
- Micro Recall: 0.6631428571428571
- Weighted Recall: 0.6631428571428571


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/nihaldsouza1/autonlp-yelp-rating-classification-545015430
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("nihaldsouza1/autonlp-yelp-rating-classification-545015430", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("nihaldsouza1/autonlp-yelp-rating-classification-545015430", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```