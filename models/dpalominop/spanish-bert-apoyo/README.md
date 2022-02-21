```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

tokenizer = AutoTokenizer.from_pretrained("dpalominop/spanish-bert-apoyo")
model = AutoModelForSequenceClassification.from_pretrained("dpalominop/spanish-bert-apoyo")
```