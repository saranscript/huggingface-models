---
tags: autonlp
language: en
widget:
- text: "I love AutoNLP 🤗"
datasets:
- test123/autonlp-data-ingredient_pseudo_label_training_ner
co2_eq_emissions: 129.63722838909717
---

# Model Trained Using AutoNLP

- Problem type: Entity Extraction
- Model ID: 29576765
- CO2 Emissions (in grams): 129.63722838909717

## Validation Metrics

- Loss: 0.0062578353099524975
- Accuracy: 0.9982143458254896
- Precision: 0.9832763577033642
- Recall: 0.9849215922798552
- F1: 0.9840982873583328

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/test123/autonlp-ingredient_pseudo_label_training_ner-29576765
```

Or Python API:

```
from transformers import AutoModelForTokenClassification, AutoTokenizer

model = AutoModelForTokenClassification.from_pretrained("test123/autonlp-ingredient_pseudo_label_training_ner-29576765", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("test123/autonlp-ingredient_pseudo_label_training_ner-29576765", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```