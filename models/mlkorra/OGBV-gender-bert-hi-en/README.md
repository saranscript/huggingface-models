## BERT Model for OGBV gendered text classification 


## How to use
```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
  
tokenizer = AutoTokenizer.from_pretrained("mlkorra/OGBV-gender-bert-hi-en")

model = AutoModelForSequenceClassification.from_pretrained("mlkorra/OGBV-gender-bert-hi-en")
```

## Model Performance

|Metric|dev|test| 
|---|--|--|
|Accuracy|0.88|0.81|
|F1(weighted)|0.86|0.80|
