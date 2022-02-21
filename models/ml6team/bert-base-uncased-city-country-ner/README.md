---
language:
- en
tags:
- token-classification
- address-NER
- NER
- bert-base-uncased

datasets:
- Ultra Fine Entity Typing
metrics:
- Precision
- Recall
- F1 Score

widget:
- text: "Hi, I am Kermit and I live in Berlin"
- text: "It is very difficult to find a house in Berlin, Germany."
- text: "ML6 is a very cool company from Belgium"
- text: "Samuel ppops in a happy plce called Berlin which happens to be Kazakhstan"
- text: "My family and I visited Montreal, Canada last week and the flight from Amsterdam took 9 hours"



---



## City-Country-NER

A `bert-base-uncased` model finetuned on a custom dataset to detect `Country` and `City` names from a given sentence. 

### Custom Dataset
We weakly supervised the [Ultra-Fine Entity Typing](https://www.cs.utexas.edu/~eunsol/html_pages/open_entity.html) dataset to include the `City` and `Country` information. We also did some extra preprocessing to remove false labels. 

The model predicts 3 different tags: `OTHER`, `CITY` and `COUNTRY`



### How to use the finetuned model?

```
from transformers import AutoTokenizer, AutoModelForTokenClassification

tokenizer = AutoTokenizer.from_pretrained("ml6team/bert-base-uncased-city-country-ner")

model = AutoModelForTokenClassification.from_pretrained("ml6team/bert-base-uncased-city-country-ner")

from transformers import pipeline

nlp = pipeline('ner', model=model, tokenizer=tokenizer, aggregation_strategy="simple")
nlp("My name is Kermit and I live in London.")
```