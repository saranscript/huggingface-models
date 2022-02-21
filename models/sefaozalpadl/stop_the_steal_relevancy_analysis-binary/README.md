---
tags: coe
language: en
widget:
- text: "take our country back. Stop the steal! #trump2020"
datasets:
- sefaozalpadl/autonlp-data-stop_the_steal_relevancy_analysis
co2_eq_emissions: 0.6503024714880831
---

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 23995359
- CO2 Emissions (in grams): 0.6503024714880831

## Validation Metrics

- Loss: 0.49598395824432373
- Accuracy: 0.7907801418439716
- Precision: 0.7841726618705036
- Recall: 0.7898550724637681
- AUC: 0.8774154589371981
- F1: 0.7870036101083032

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/sefaozalpadl/stop_the_steal_relevancy_analysis-binary
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("sefaozalpadl/stop_the_steal_relevancy_analysis-binary", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("sefaozalpadl/stop_the_steal_relevancy_analysis-binary", use_auth_token=True)

inputs = tokenizer("take our country back. Stop the steal! #trump2020", return_tensors="pt")

outputs = model(**inputs)
```