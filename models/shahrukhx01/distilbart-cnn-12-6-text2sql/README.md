The distilbart-cnn-12-6-text2sql is fine-tuned on WIKISQL dataset.
```python
from transformers import BartTokenizer, BartForConditionalGeneration, BartConfig

model = BartForConditionalGeneration.from_pretrained('shahrukhx01/distilbart-cnn-12-6-text2sql')
tokenizer = BartTokenizer.from_pretrained('shahrukhx01/distilbart-cnn-12-6-text2sql')

TEXT_QUERY = "what is the temperature of berlin "
inputs = tokenizer([TEXT_QUERY], max_length=1024, return_tensors='pt')

# Generate SQL
text_query_ids = model.generate(inputs['input_ids'], num_beams=4, max_length=5, early_stopping=True)
print([tokenizer.decode(g, skip_special_tokens=True, clean_up_tokenization_spaces=False) for g in text_query_ids])
```