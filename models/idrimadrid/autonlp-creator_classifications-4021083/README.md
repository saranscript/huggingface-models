---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- idrimadrid/autonlp-data-creator_classifications
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 4021083

## Validation Metrics

- Loss: 0.6848716735839844
- Accuracy: 0.8825910931174089
- Macro F1: 0.41301646762109634
- Micro F1: 0.8825910931174088
- Weighted F1: 0.863740586166105
- Macro Precision: 0.4129337301330573
- Micro Precision: 0.8825910931174089
- Weighted Precision: 0.8531335941587811
- Macro Recall: 0.44466614072309585
- Micro Recall: 0.8825910931174089
- Weighted Recall: 0.8825910931174089


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/idrimadrid/autonlp-creator_classifications-4021083
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("idrimadrid/autonlp-creator_classifications-4021083", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("idrimadrid/autonlp-creator_classifications-4021083", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```