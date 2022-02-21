---
tags: autonlp
language: en
widget:
- text: "I am still waiting on my card?"
datasets:
- banking77
model-index:
- name: BERT-Banking77
  results:
  - task: 
      name: Text Classification
      type: text-classification
    dataset:
      name: "BANKING77" 
      type: banking77
    metrics:
       - name: Accuracy
         type: accuracy
         value: 93.64
       - name: Macro F1
         type: macro-f1
         value: 93.65
       - name: Weighted F1
         type: weighted-f1
         value: 93.65
---

# `BERT-Banking77` trained using autoNLP


- Problem type: Multi-class Classification

## Validation Metrics

- Loss: 0.3031957447528839
- Accuracy: 0.9363636363636364
- Macro F1: 0.9364655956915154
- Micro F1: 0.9363636363636364
- Weighted F1: 0.9364655956915157
- Macro Precision: 0.9396792003322154
- Micro Precision: 0.9363636363636364
- Weighted Precision: 0.9396792003322155
- Macro Recall: 0.9363636363636365
- Micro Recall: 0.9363636363636364
- Weighted Recall: 0.9363636363636364


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I am still waiting on my card?"}' https://api-inference.huggingface.co/models/philschmid/BERT-Banking77
```

Or Python API:

```
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

model_id = 'philschmid/BERT-Banking77'
tokenizer = AutoTokenizer.from_pretrained(model_id)

model = AutoModelForSequenceClassification.from_pretrained(model_id)
classifier = pipeline('text-classification', tokenizer=tokenizer, model=model)
classifier('What is the base of the exchange rates?')
```