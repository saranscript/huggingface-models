---
tags: autonlp
language: en
widget:
- text: "Worry is a down payment on a problem you may never have'. Joyce Meyer.  #motivation #leadership #worry"
datasets:
- tweet_eval
model-index:
- name: BERT-tweet-eval-emotion
  results:
  - task: 
      name: Sentiment Analysis
      type: sentiment-analysis
    dataset:
      name: "tweeteval" 
      type: tweet-eval
    metrics:
       - name: Accuracy
         type: accuracy
         value: 81.00
       - name: Macro F1
         type: macro-f1
         value: 77.37
       - name: Weighted F1
         type: weighted-f1
         value: 80.63
---
# `BERT-tweet-eval-emotion` trained using autoNLP
- Problem type: Multi-class Classification

## Validation Metrics

- Loss: 0.5408923625946045
- Accuracy: 0.8099929627023223
- Macro F1: 0.7737195387641751
- Micro F1: 0.8099929627023222
- Weighted F1: 0.8063100677512649
- Macro Precision: 0.8083955817268176
- Micro Precision: 0.8099929627023223
- Weighted Precision: 0.8104009668394634
- Macro Recall: 0.7529197049888299
- Micro Recall: 0.8099929627023223
- Weighted Recall: 0.8099929627023223

## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "Worry is a down payment on a problem you may never have'. Joyce Meyer.  #motivation #leadership #worry"}' https://api-inference.huggingface.co/models/philschmid/BERT-tweet-eval-emotion
```

Or Python API:

```py
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

model_id = 'philschmid/BERT-tweet-eval-emotion'

tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForSequenceClassification.from_pretrained(model_id)

classifier = pipeline('text-classification', tokenizer=tokenizer, model=model)
classifier("Worry is a down payment on a problem you may never have'. Joyce Meyer.  #motivation #leadership #worry")
```