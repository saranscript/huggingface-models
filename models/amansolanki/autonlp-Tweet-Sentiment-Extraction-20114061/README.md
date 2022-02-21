---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- amansolanki/autonlp-data-Tweet-Sentiment-Extraction
co2_eq_emissions: 3.651199395353127
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 20114061
- CO2 Emissions (in grams): 3.651199395353127

## Validation Metrics

- Loss: 0.5046541690826416
- Accuracy: 0.8036219581211093
- Macro F1: 0.807095210403678
- Micro F1: 0.8036219581211093
- Weighted F1: 0.8039634739225368
- Macro Precision: 0.8076842795233988
- Micro Precision: 0.8036219581211093
- Weighted Precision: 0.8052135235094771
- Macro Recall: 0.8075241470527056
- Micro Recall: 0.8036219581211093
- Weighted Recall: 0.8036219581211093


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/amansolanki/autonlp-Tweet-Sentiment-Extraction-20114061
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("amansolanki/autonlp-Tweet-Sentiment-Extraction-20114061", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("amansolanki/autonlp-Tweet-Sentiment-Extraction-20114061", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```