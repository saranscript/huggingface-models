---
tags: autonlp
language: en
widget:
- text: "I am still waiting on my card?"
datasets:
- banking77
model-index:
- name: RoBERTa-Banking77
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
         value: 93.51
       - name: Macro F1
         type: macro-f1
         value: 93.49
       - name: Weighted F1
         type: weighted-f1
         value: 93.49
---
# `RoBERTa-Banking77` trained using autoNLP


- Problem type: Multi-class Classification

## Validation Metrics

- Loss: 0.27382662892341614
- Accuracy: 0.935064935064935
- Macro F1: 0.934939412967268
- Micro F1: 0.935064935064935
- Weighted F1: 0.934939412967268
- Macro Precision: 0.9372295644352715
- Micro Precision: 0.935064935064935
- Weighted Precision: 0.9372295644352717
- Macro Recall: 0.9350649350649349
- Micro Recall: 0.935064935064935
- Weighted Recall: 0.935064935064935


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "I love AutoNLP"}' https://api-inference.huggingface.co/models/philschmid/RoBERTa-Banking77
```

Or Python API:

```py
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

model_id = 'philschmid/RoBERTa-Banking77'
tokenizer = AutoTokenizer.from_pretrained(model_id)

model = AutoModelForSequenceClassification.from_pretrained(model_id)
classifier = pipeline('text-classification', tokenizer=tokenizer, model=model)
classifier('What is the base of the exchange rates?')
```