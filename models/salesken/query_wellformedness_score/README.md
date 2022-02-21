---
tags: salesken
license: apache-2.0
inference: true

datasets: google_wellformed_query

widget:
 - text: "what was the reason for everyone for leave the company"
---

This model evaluates the wellformedness (non-fragment, grammatically correct)  score of a sentence. Model is case-sensitive and penalises for incorrect case and grammar as well. 

['She is presenting a paper tomorrow','she is presenting a paper tomorrow','She present paper today']

[[0.8917],[0.4270],[0.0134]]
```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
tokenizer = AutoTokenizer.from_pretrained("salesken/query_wellformedness_score")
model = AutoModelForSequenceClassification.from_pretrained("salesken/query_wellformedness_score")
sentences = [' what was the reason for everyone to leave the company ', 
               ' What was the reason behind everyone leaving the company ', 
               ' why was everybody leaving the company ', 
               ' what was the reason to everyone leave the company ',
               ' what be the reason for everyone to leave the company ', 
               ' what was the reasons for everyone to leave the company ', 
               ' what were the reasons for everyone to leave the company ']

features = tokenizer(sentences,  padding=True, truncation=True, return_tensors="pt")
model.eval()
with torch.no_grad():
    scores = model(**features).logits
print(scores)

```


