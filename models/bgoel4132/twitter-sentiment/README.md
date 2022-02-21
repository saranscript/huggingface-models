---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- bgoel4132/autonlp-data-twitter-sentiment
co2_eq_emissions: 186.8637425115097
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 35868888
- CO2 Emissions (in grams): 186.8637425115097

## Validation Metrics

- Loss: 0.2020547091960907
- Accuracy: 0.9233253193796257
- Macro F1: 0.9240407542958707
- Micro F1: 0.9233253193796257
- Weighted F1: 0.921800586774046
- Macro Precision: 0.9432284179846658
- Micro Precision: 0.9233253193796257
- Weighted Precision: 0.9247263361914827
- Macro Recall: 0.9139437626409382
- Micro Recall: 0.9233253193796257
- Weighted Recall: 0.9233253193796257


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/bgoel4132/autonlp-twitter-sentiment-35868888
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("bgoel4132/autonlp-twitter-sentiment-35868888", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("bgoel4132/autonlp-twitter-sentiment-35868888", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```