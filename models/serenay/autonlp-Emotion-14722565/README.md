---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- serenay/autonlp-data-Emotion
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 14722565

## Validation Metrics

- Loss: 0.6077525615692139
- Accuracy: 0.7745398773006135
- Macro F1: 0.7287152925396537
- Micro F1: 0.7745398773006135
- Weighted F1: 0.7754701717098939
- Macro Precision: 0.7282186282186283
- Micro Precision: 0.7745398773006135
- Weighted Precision: 0.7787550922520248
- Macro Recall: 0.7314173610899214
- Micro Recall: 0.7745398773006135
- Weighted Recall: 0.7745398773006135


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/serenay/autonlp-Emotion-14722565
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("serenay/autonlp-Emotion-14722565", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("serenay/autonlp-Emotion-14722565", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```