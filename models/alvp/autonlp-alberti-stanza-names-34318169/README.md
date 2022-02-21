---
tags: autonlp
language: unk
widget:
- text: "I love AutoNLP 🤗"
datasets:
- alvp/autonlp-data-alberti-stanza-names
co2_eq_emissions: 8.612473981829835
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 34318169
- CO2 Emissions (in grams): 8.612473981829835

## Validation Metrics

- Loss: 1.3520570993423462
- Accuracy: 0.6083916083916084
- Macro F1: 0.5420169617715481
- Micro F1: 0.6083916083916084
- Weighted F1: 0.5963328136975058
- Macro Precision: 0.5864033493660455
- Micro Precision: 0.6083916083916084
- Weighted Precision: 0.6364793882921277
- Macro Recall: 0.5545405576555766
- Micro Recall: 0.6083916083916084
- Weighted Recall: 0.6083916083916084


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/alvp/autonlp-alberti-stanza-names-34318169
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("alvp/autonlp-alberti-stanza-names-34318169", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("alvp/autonlp-alberti-stanza-names-34318169", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```