---
tags: autonlp
language: en
widget:
- text: "the jews have a lot of power"
datasets:
- astarostap/autonlp-data-antisemitism-2
co2_eq_emissions: 2.0686690092905224
---

# Description

This model takes a tweet with the word "jew" in it, and determines if it's antisemitic.

Training data:

This model was trained on 4k tweets, where ~50% were labeled as antisemitic.

I labeled them myself based on personal experience and knowledge about common antisemitic tropes.

Note:

The goal for this model is not to be used as a final say on what is or is not antisemitic, but rather as a first pass on what might be antisemitic and should be reviewed by human experts.

Please keep in mind that I'm not an expert on antisemitism or hatespeech.

Whether something is antisemitic or not depends on the context, as for any hate speech, and everyone has a different definition for what is hate speech.

If you would like to collaborate on antisemitism detection, please feel free to contact me at starosta@alumni.stanford.edu

This model is not ready for production, it needs more evaluation and more training data.

# Model Trained Using AutoNLP

- Problem type: Binary Classification
- Model ID: 21194454
- CO2 Emissions (in grams): 2.0686690092905224
- Dataset: https://huggingface.co/datasets/astarostap/autonlp-data-antisemitism-2

## Validation Metrics

- Loss: 0.5291365385055542
- Accuracy: 0.7572692793931732
- Precision: 0.7126948775055679
- Recall: 0.835509138381201
- AUC: 0.8185826549941126
- F1: 0.7692307692307693

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/astarostap/autonlp-antisemitism-2-21194454
```

Or Python API:

```
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model = AutoModelForSequenceClassification.from_pretrained("astarostap/autonlp-antisemitism-2-21194454", use_auth_token=True)

tokenizer = AutoTokenizer.from_pretrained("astarostap/autonlp-antisemitism-2-21194454", use_auth_token=True)

inputs = tokenizer("I love AutoNLP", return_tensors="pt")

outputs = model(**inputs)
```