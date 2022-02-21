---
tags: autonlp
language: fr
widget:
- text: "Il y a dans ce pays une fracture"
datasets:
- mazancourt/autonlp-data-politics-sentence-classifier
co2_eq_emissions: 1.06099358268878
---

# Prediction of sentence "nature" in a French political sentence

This model aims at predicting the nature of a sentence in a French political sentence.
The predictions fall in three categories:
- `problem`: the sentence describes a problem (usually to be tackled by the speaker), for example _il y a dans ce pays une fracture_ (J. Chirac)
- `solution`: the sentences describes a solution (typically part of a political programme), for example: _J’ai supprimé les droits de succession parce que je crois au travail et parce que je crois à la famille._ (N. Sarkozy)
- `other`: the sentence does not belong to any of these categories, for example: _vive la République, vive la France_

This model was trained using AutoNLP based on sentences extracted from a mix of political tweets and speeches.

# Model Trained Using AutoNLP

- Problem type: Multi-class Classification
- Model ID: 23105051
- CO2 Emissions (in grams): 1.06099358268878

## Validation Metrics

- Loss: 0.6050735712051392
- Accuracy: 0.8097826086956522
- Macro F1: 0.7713543865034599
- Micro F1: 0.8097826086956522
- Weighted F1: 0.8065488494385247
- Macro Precision: 0.7861074705111403
- Micro Precision: 0.8097826086956522
- Weighted Precision: 0.806470454156932
- Macro Recall: 0.7599656456873758
- Micro Recall: 0.8097826086956522
- Weighted Recall: 0.8097826086956522


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "Il y a dans ce pays une fracture"}' https://api-inference.huggingface.co/models/mazancourt/politics-sentence-classifier
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("mazancourt/autonlp-politics-sentence-classifier-23105051", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("mazancourt/politics-sentence-classifier", use_auth_token=True)

inputs = tokenizer("Il y a dans ce pays une fracture", return_tensors="pt")

outputs = model(**inputs)

# Category can be "problem", "solution" or "other"
category = outputs[0]["label"]
score = outputs[0]["score"]
```