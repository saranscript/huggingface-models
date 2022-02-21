---
language: "en"
thumbnail: "https://huggingface.co/sampathkethineedi"
tags:
- distilbert
- pytorch
- tensorflow
- text-classification
- industry
- buisiness
- description
- multi-class 
- classification
liscence: "mit"
inference: false
---

# industry-classification

## Model description

DistilBERT Model to classify a business description into one of **62 industry tags**. 
Trained on 7000 samples of Business Descriptions and associated labels of companies in India.

## How to use

PyTorch and TF models available

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

tokenizer = AutoTokenizer.from_pretrained("sampathkethineedi/industry-classification")  
model = AutoModelForSequenceClassification.from_pretrained("sampathkethineedi/industry-classification")

industry_tags = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)
industry_tags("Stellar Capital Services Limited is an India-based non-banking financial company ... loan against property, management consultancy, personal loans and unsecured loans.")

'''Ouput'''
[{'label': 'Consumer Finance', 'score': 0.9841355681419373}]
```

## Limitations and bias
Training data is only for Indian companies
