---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- rexxar96/autonlp-data-roberta-large-finetuned
co2_eq_emissions: 73.72876780772296
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 467612250
- CO2 Emissions (in grams): 73.72876780772296

## Validation Metrics

- Loss: 0.18261319398880005
- Accuracy: 0.9541659567217584
- Precision: 0.9530625832223701
- Recall: 0.9572049481778669
- AUC: 0.9901737875196123
- F1: 0.9551292743953294

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/rexxar96/autonlp-roberta-large-finetuned-467612250
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("rexxar96/autonlp-roberta-large-finetuned-467612250", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("rexxar96/autonlp-roberta-large-finetuned-467612250", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```