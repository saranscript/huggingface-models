---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- juliensimon/autonlp-data-song-lyrics
co2_eq_emissions: 55.552987716859484
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 18753423
- CO2 Emissions (in grams): 55.552987716859484

## Validation Metrics

- Loss: 0.913820743560791
- Accuracy: 0.654110224531453
- Macro F1: 0.5327761649415296
- Micro F1: 0.654110224531453
- Weighted F1: 0.6339481529454227
- Macro Precision: 0.6799297267808116
- Micro Precision: 0.654110224531453
- Weighted Precision: 0.6533459269990771
- Macro Recall: 0.49907494605289154
- Micro Recall: 0.654110224531453
- Weighted Recall: 0.654110224531453


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/juliensimon/autonlp-song-lyrics-18753423
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("juliensimon/autonlp-song-lyrics-18753423", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("juliensimon/autonlp-song-lyrics-18753423", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```