---
language:
- da
tags:
- bert
- pytorch
- sentiment
- polarity
license: cc-by-sa-4.0
datasets:
- Twitter Sentiment
- Europarl Sentiment
metrics:
- f1
widget:
- text: Det er super godt
---

# Danish BERT Tone for sentiment polarity detection

The BERT Tone model detects sentiment polarity (positive, neutral or negative) in Danish texts. 
It has been finetuned on the pretrained [Danish BERT](https://github.com/certainlyio/nordic_bert) model by BotXO. 

See the [DaNLP documentation](https://danlp-alexandra.readthedocs.io/en/latest/docs/tasks/sentiment_analysis.html#bert-tone) for more details. 


Here is how to use the model:

```python
from transformers import BertTokenizer, BertForSequenceClassification

model = BertForSequenceClassification.from_pretrained("DaNLP/da-bert-tone-sentiment-polarity")
tokenizer = BertTokenizer.from_pretrained("DaNLP/da-bert-tone-sentiment-polarity")
```

## Training data

The data used for training come from the [Twitter Sentiment](https://danlp-alexandra.readthedocs.io/en/latest/docs/datasets.html#twitsent) and [EuroParl sentiment 2](https://danlp-alexandra.readthedocs.io/en/latest/docs/datasets.html#europarl-sentiment2) datasets.

