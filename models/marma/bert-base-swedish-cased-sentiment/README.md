Experimental sentiment analysis based on ~20k of App Store reviews in Swedish.

### Usage
```python
from transformers import pipeline

>>> sa = pipeline('sentiment-analysis', model='marma/bert-base-swedish-cased-sentiment')
>>> sa('Det här är ju fantastiskt!')
[{'label': 'POSITIVE', 'score': 0.9974609613418579}]

>>> sa('Den här appen suger!')
[{'label': 'NEGATIVE', 'score': 0.998340368270874}]

>>> sa('Det är fruktansvärt.')
[{'label': 'NEGATIVE', 'score': 0.998340368270874}]

>>> sa('Det är fruktansvärt bra.')
[{'label': 'POSITIVE', 'score': 0.998340368270874}]
```