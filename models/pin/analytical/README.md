---
language: da
tags:
- danish
- bert
- sentiment
- analytical
license: cc-by-4.0
widget:
- text: "Jeg synes, det er en elendig film"
---
# Danish BERT fine-tuned for Detecting 'Analytical'

This model detects if a Danish text is 'subjective' or 'objective'.

It is trained and tested on Tweets and texts transcribed from the European Parliament annotated by [Alexandra Institute](https://github.com/alexandrainst). The model is trained with the [`senda`](https://github.com/ebanalyse/senda) package.

Here is an example of how to load the model in PyTorch using the [🤗Transformers](https://github.com/huggingface/transformers) library:

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline
tokenizer = AutoTokenizer.from_pretrained("pin/analytical")
model = AutoModelForSequenceClassification.from_pretrained("pin/analytical")

# create 'senda' sentiment analysis pipeline 
analytical_pipeline = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)

text = "Jeg synes, det er en elendig film"
# in English: 'I think, it is a terrible movie'
analytical_pipeline(text)
```

## Performance 
The `senda` model achieves an accuracy of 0.89 and a macro-averaged F1-score of 0.78 on a small test data set, that [Alexandra Institute](https://github.com/alexandrainst/danlp/blob/master/docs/docs/datasets.md#twitter-sentiment) provides. The model can most certainly be improved, and we encourage all NLP-enthusiasts to give it their best shot - you can use the [`senda`](https://github.com/ebanalyse/senda) package to do this.

#### Contact
Feel free to contact author Lars Kjeldgaard on [lars.kjeldgaard@eb.dk](mailto:lars.kjeldgaard@eb.dk).


