---
tags:
- wikisql
- text2sql
---
```python
from transformers import BartTokenizer, BartForConditionalGeneration, BartConfig
model = BartForConditionalGeneration.from_pretrained('shahrukhx01/schema-aware-distilbart-cnn-12-6-text2sql')
tokenizer = BartTokenizer.from_pretrained('shahrukhx01/schema-aware-distilbart-cnn-12-6-text2sql')
## add NL query with table schema
question = "What is terrence ross' nationality? </s> <col0> Player : text <col1> No. : text <col2> Nationality : text <col3> Position : text <col4> Years in Toronto : text <col5>  School/Club Team : text"

inputs = tokenizer([question], max_length=1024, return_tensors='pt')

# Generate SQL
text_query_ids = model.generate(inputs['input_ids'], num_beams=4, min_length=0, max_length=125, early_stopping=True)
prediction = [tokenizer.decode(g, skip_special_tokens=True, clean_up_tokenization_spaces=False) for g in text_query_ids][0]
print(prediction)
```