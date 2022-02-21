---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- madhurjindal/autonlp-data-Gibberish-Detector
co2_eq_emissions: 5.527544460835904
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 492513457
- CO2 Emissions (in grams): 5.527544460835904

## Validation Metrics

- Loss: 0.07609463483095169
- Accuracy: 0.9735624586913417
- Macro F1: 0.9736173135739408
- Micro F1: 0.9735624586913417
- Weighted F1: 0.9736173135739408
- Macro Precision: 0.9737771415197378
- Micro Precision: 0.9735624586913417
- Weighted Precision: 0.9737771415197378
- Macro Recall: 0.9735624586913417
- Micro Recall: 0.9735624586913417
- Weighted Recall: 0.9735624586913417


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/madhurjindal/autonlp-Gibberish-Detector-492513457
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("madhurjindal/autonlp-Gibberish-Detector-492513457", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("madhurjindal/autonlp-Gibberish-Detector-492513457", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```