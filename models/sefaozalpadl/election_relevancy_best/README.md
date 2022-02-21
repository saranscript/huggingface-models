---
tags: coe
language: en
widget:
- text: "@PressSec Response to Putin is laughable. He has Biden's number. He knows Biden can't hold up in a live debate, and the Chinese did a number on the U.S. too. Biden is making US the laughing stock of the world. We pay the price for a stolen election"
datasets:
- sefaozalpadl/autonlp-data-election_relevancy_analysis
co2_eq_emissions: 1.3248523193990855
---

# Election Fraud Binary Classifier

- Problem type: Binary Classification
- Model ID: 23315155
- CO2 Emissions (in grams): 1.3248523193990855

## Validation Metrics

- Loss: 0.4240806996822357
- Accuracy: 0.8173913043478261
- Precision: 0.8837209302325582
- Recall: 0.8085106382978723
- AUC: 0.8882580285281696
- F1: 0.8444444444444444

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/sefaozalpadl/election_relevancy_best
```

Or Python API:

```
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("sefaozalpadl/election_relevancy_best")

model = AutoModelForSequenceClassification.from_pretrained("sefaozalpadl/election_relevancy_best")

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```