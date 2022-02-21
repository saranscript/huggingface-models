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
# Danish BERT fine-tuned for Sentiment Analysis with  `senda`

This model detects polarity ('positive', 'neutral', 'negative') of Danish texts.

It is trained and tested on Tweets annotated by [Alexandra Institute](https://github.com/alexandrainst). The model is trained with the [`senda`](https://github.com/ebanalyse/senda) package.

Here is an example of how to load the model in PyTorch using the [🤗Transformers](https://github.com/huggingface/transformers) library:

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification, pipeline
tokenizer = AutoTokenizer.from_pretrained("pin/senda")
model = AutoModelForSequenceClassification.from_pretrained("pin/senda")

# create 'senda' sentiment analysis pipeline 
senda_pipeline = pipeline('sentiment-analysis', model=model, tokenizer=tokenizer)

text = "Sikke en dejlig dag det er i dag"
# in English: 'what a lovely day'
senda_pipeline(text)
```

## Performance 
The `senda` model achieves an accuracy of 0.77 and a macro-averaged F1-score of 0.73 on a small test data set, that [Alexandra Institute](https://github.com/alexandrainst/danlp/blob/master/docs/docs/datasets.md#twitter-sentiment) provides. The model can most certainly be improved, and we encourage all NLP-enthusiasts to give it their best shot - you can use the [`senda`](https://github.com/ebanalyse/senda) package to do this.

#### Contact
Feel free to contact author Lars Kjeldgaard on [lars.kjeldgaard@eb.dk](mailto:lars.kjeldgaard@eb.dk).

#### Shout-outs

Props to [Malte Højmark-Berthelsen](mailto:hjb@kmd.dk) for pretraining Danish BERT and helping out adding a TensorFlow backend for `senda`.
