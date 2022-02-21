---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- rodrigogelacio/autonlp-data-department-classification
co2_eq_emissions: 1.4862856774320061
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 534915130
- CO2 Emissions (in grams): 1.4862856774320061

## Validation Metrics

- Loss: 0.37066277861595154
- Accuracy: 0.9204545454545454
- Macro F1: 0.9103715740678612
- Micro F1: 0.9204545454545455
- Weighted F1: 0.9196871607509906
- Macro Precision: 0.9207759152612094
- Micro Precision: 0.9204545454545454
- Weighted Precision: 0.922177301864802
- Macro Recall: 0.9055002187355129
- Micro Recall: 0.9204545454545454
- Weighted Recall: 0.9204545454545454


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/rodrigogelacio/autonlp-department-classification-534915130
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("rodrigogelacio/autonlp-department-classification-534915130", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("rodrigogelacio/autonlp-department-classification-534915130", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```