---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- vinaydngowda/autonlp-data-case-classify-xlnet
co2_eq_emissions: 19.964760910364927
---

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 496213536
- CO2 Emissions (in grams): 19.964760910364927

## Validation Metrics

- Loss: 0.7149562835693359
- Accuracy: 0.8092592592592592
- Macro F1: 0.8085189591849891
- Micro F1: 0.8092592592592593
- Weighted F1: 0.8085189591849888
- Macro Precision: 0.8137745564384112
- Micro Precision: 0.8092592592592592
- Weighted Precision: 0.8137745564384112
- Macro Recall: 0.8092592592592592
- Micro Recall: 0.8092592592592592
- Weighted Recall: 0.8092592592592592


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/vinaydngowda/autonlp-case-classify-xlnet-496213536
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("vinaydngowda/autonlp-case-classify-xlnet-496213536", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("vinaydngowda/autonlp-case-classify-xlnet-496213536", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```