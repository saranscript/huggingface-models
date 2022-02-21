---
tags: autonlp
language: en
widget:
- text: "Worry is a down payment on a problem you may never have'. Joyce Meyer.  #motivation #leadership #worry"
datasets:
- tweet_eval
model-index:
- name: DistilBERT-tweet-eval-emotion
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
         value: 80.59
       - name: Macro F1
         type: macro-f1
         value: 78.17
       - name: Weighted F1
         type: weighted-f1
         value: 80.11
---
# `DistilBERT-tweet-eval-emotion` trained using autoNLP
- Problem type: Multi-class Classification

## Validation Metrics

- Loss: 0.5564454197883606
- Accuracy: 0.8057705840957072
- Macro F1: 0.7536021792986777
- Micro F1: 0.8057705840957073
- Weighted F1: 0.8011390170248318
- Macro Precision: 0.7817458823222652
- Micro Precision: 0.8057705840957072
- Weighted Precision: 0.8025156844840151
- Macro Recall: 0.7369154685020982
- Micro Recall: 0.8057705840957072
- Weighted Recall: 0.8057705840957072


## Usage

You can use cURL to access this model:

```
$ curl -X POST -H "Authorization: Bearer YOUR_API_KEY" -H "Content-Type: application/json" -d '{"inputs": "Worry is a down payment on a problem you may never have'. Joyce Meyer.  #motivation #leadership #worry"}' https://api-inference.huggingface.co/models/philschmid/autonlp-tweet_eval_vs_comprehend-3092245
```

Or Python API:

```py
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline

model_id = 'philschmid/DistilBERT-tweet-eval-emotion'

tokenizer = AutoTokenizer.from_pretrained(model_id)
model = AutoModelForSequenceClassification.from_pretrained(model_id)

classifier = pipeline('text-classification', tokenizer=tokenizer, model=model)
classifier("Worry is a down payment on a problem you may never have'. Joyce Meyer.  #motivation #leadership #worry")
```