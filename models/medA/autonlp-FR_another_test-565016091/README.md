---
tags: autonlp
language: fr
widget:
- text: "I love AutoNLP 🤗"
datasets:
- medA/autonlp-data-FR_another_test
co2_eq_emissions: 70.54639641012226
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 565016091
- CO2 Emissions (in grams): 70.54639641012226

## Validation Metrics

- Loss: 0.5170354247093201
- Accuracy: 0.8545909432074056
- Macro F1: 0.7910662503820883
- Micro F1: 0.8545909432074056
- Weighted F1: 0.8539837213761081
- Macro Precision: 0.8033640381948799
- Micro Precision: 0.8545909432074056
- Weighted Precision: 0.856160322286008
- Macro Recall: 0.7841845637031052
- Micro Recall: 0.8545909432074056
- Weighted Recall: 0.8545909432074056


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/medA/autonlp-FR_another_test-565016091
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("medA/autonlp-FR_another_test-565016091", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("medA/autonlp-FR_another_test-565016091", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```