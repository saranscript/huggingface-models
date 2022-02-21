---
tags: autonlp
language: ja
widget:
- text: "I love AutoNLP 🤗"
datasets:
- trtd56/autonlp-data-wrime_joy_only
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 117396

## Validation Metrics

- Loss: 0.4094310998916626
- Accuracy: 0.8201678240740741
- Precision: 0.6750303520841765
- Recall: 0.7912713472485768
- AUC: 0.8927167943538512
- F1: 0.728543350076436

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/trtd56/autonlp-wrime_joy_only-117396
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("trtd56/autonlp-wrime_joy_only-117396", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("trtd56/autonlp-wrime_joy_only-117396", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```