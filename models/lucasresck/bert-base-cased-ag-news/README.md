---
language:
- en
license: mit
tags:
- bert
- classification
datasets:
- ag_news
metrics:
- accuracy
- f1
- recall
- precision
widget:
- text: "Is it soccer or football?"
  example_title: "Sports"
- text: "A new version of Ubuntu was released."
  example_title: "Sci/Tech"
---

# bert-base-cased-ag-news

BERT model fine-tuned on AG News classification dataset using a linear layer on top of the [CLS] token output, with 0.945 test accuracy.

### How to use

Here is how to use this model to classify a given text:
```python
from transformers import AutoTokenizer, BertForSequenceClassification
tokenizer = AutoTokenizer.from_pretrained('lucasresck/bert-base-cased-ag-news')
model = BertForSequenceClassification.from_pretrained('lucasresck/bert-base-cased-ag-news')
text = "Is it soccer or football?"
encoded_input = tokenizer(text, return_tensors='pt', truncation=True, max_length=512)
output = model(**encoded_input)
```

### Limitations and bias

Bias were not assessed in this model, but, considering that pre-trained BERT is known to carry bias, it is also expected for this model. BERT's authors say: "This bias will also affect all fine-tuned versions of this model."

## Evaluation results

```
              precision    recall  f1-score   support

           0     0.9539    0.9584    0.9562      1900
           1     0.9884    0.9879    0.9882      1900
           2     0.9251    0.9095    0.9172      1900
           3     0.9127    0.9242    0.9184      1900

    accuracy                         0.9450      7600
   macro avg     0.9450    0.9450    0.9450      7600
weighted avg     0.9450    0.9450    0.9450      7600
```
