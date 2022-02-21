---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- kamivao/autonlp-data-entity_selection
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 5771228

## Validation Metrics

- Loss: 0.17127291858196259
- Accuracy: 0.9206671174216813
- Precision: 0.9588885738588036
- Recall: 0.9423237670660352
- AUC: 0.9720189638675828
- F1: 0.9505340078695896

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/kamivao/autonlp-entity_selection-5771228
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("kamivao/autonlp-entity_selection-5771228", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("kamivao/autonlp-entity_selection-5771228", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```