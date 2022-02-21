---
language:
- da
tags:
- bert
- pytorch
- subjectivity
- objectivity
license: cc-by-sa-4.0
datasets:
- Twitter Sentiment
- Europarl Sentiment
widget:
- text: Jeg tror alligvel, det bliver godt
metrics:
- f1
---

# Danish BERT Tone for the detection of subjectivity/objectivity

The BERT Tone model detects whether a text (in Danish) is subjective or objective. 
The model is based on the finetuning of the pretrained [Danish BERT](https://github.com/certainlyio/nordic_bert) model by BotXO. 

See the [DaNLP documentation](https://danlp-alexandra.readthedocs.io/en/latest/docs/tasks/sentiment_analysis.html#bert-tone) for more details. 


Here is how to use the model:

```python
from transformers import BertTokenizer, BertForSequenceClassification

model = BertForSequenceClassification.from_pretrained("DaNLP/da-bert-tone-subjective-objective")
tokenizer = BertTokenizer.from_pretrained("DaNLP/da-bert-tone-subjective-objective")
```

## Training data

The data used for training come from the [Twitter Sentiment](https://danlp-alexandra.readthedocs.io/en/latest/docs/datasets.html#twitsent) and [EuroParl sentiment 2](https://danlp-alexandra.readthedocs.io/en/latest/docs/datasets.html#europarl-sentiment2) datasets.

