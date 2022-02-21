---
tags: autonlp
language: en
widget:
- text: "I am still waiting on my card?"
datasets:
- banking77
model-index:
- name: DistilBERT-Banking77
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
         value: 92.47
       - name: Macro F1
         type: macro-f1
         value: 92.46
       - name: Weighted F1
         type: weighted-f1
         value: 92.46
---
# `DistilBERT-Banking77` trained using autoNLP

- Problem type: Multi-class Classification

## Validation Metrics

- Loss: 0.2988220155239105
- Accuracy: 0.9246753246753247
- Macro F1: 0.9246117406953515
- Micro F1: 0.9246753246753247
- Weighted F1: 0.9246117406953518
- Macro Precision: 0.9278163684429038
- Micro Precision: 0.9246753246753247
- Weighted Precision: 0.927816368442904
- Macro Recall: 0.9246753246753248
- Micro Recall: 0.9246753246753247
- Weighted Recall: 0.9246753246753247


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "What is the base of the exchange rates?"}' https://api-inference.huggingface.co/models/philschmid/DistilBERT
```

Or Python API:

```py
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

model_id = 'philschmid/DistilBERT-Banking77'

tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForSequenceClassification.from_pretrained(model_id)

classifier = pipeline('text-classification', tokenizer=tokenizer, model=model)
classifier('What is the base of the exchange rates?')
```