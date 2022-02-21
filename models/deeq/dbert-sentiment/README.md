```
from transformers import BertForSequenceClassification, BertTokenizer, TextClassificationPipeline
model = BertForSequenceClassification.from_pretrained("deeq/dbert-sentiment")
tokenizer = BertTokenizer.from_pretrained("deeq/dbert")
nlp = TextClassificationPipeline(model=model, tokenizer=tokenizer)
print(nlp("좋아요"))
print(nlp("글쎄요"))
```
