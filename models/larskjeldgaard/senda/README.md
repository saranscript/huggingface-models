---
language: da
tags:
- danish
- bert
- sentiment
- polarity
license: cc-by-4.0
widget:
- text: "Sikke en dejlig dag det er i dag"
---
# Danish BERT fine-tuned for Sentiment Analysis (Polarity)
This model detects polarity ('positive', 'neutral', 'negative') of danish texts.

It is trained and tested on Tweets annotated by [Alexandra Institute](https://github.com/alexandrainst).

Here is an example on how to load the model in PyTorch using the [🤗Transformers](https://github.com/huggingface/transformers) library:

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline
tokenizer = AutoTokenizer.from_pretrained("larskjeldgaard/senda")
model = AutoModelForSequenceClassification.from_pretrained("larskjeldgaard/senda")

# create 'senda' sentiment analysis pipeline 
senda_pipeline = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)

senda_pipeline("Sikke en dejlig dag det er i dag")
```
