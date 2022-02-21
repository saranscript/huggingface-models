---
language:
- da
tags:
- bert
- pytorch
- hatespeech
license: cc-by-sa-4.0
datasets:
- social media
metrics:
- f1
widget:
- text: "Senile gamle idiot"
---

# Danish BERT for hate speech classification

The BERT HateSpeech model classifies offensive Danish text into 4 categories: 
 * `Særlig opmærksomhed` (special attention, e.g. threat)
 * `Personangreb` (personal attack) 
 * `Sprogbrug` (offensive language)
 * `Spam & indhold` (spam)
This model is intended to be used after the [BERT HateSpeech detection model](https://huggingface.co/DaNLP/da-bert-hatespeech-detection).

It is based on the pretrained [Danish BERT](https://github.com/certainlyio/nordic_bert) model by BotXO which has been fine-tuned on social media data. 

See the [DaNLP documentation](https://danlp-alexandra.readthedocs.io/en/latest/docs/tasks/hatespeech.html#bertdr) for more details. 


Here is how to use the model:

```python
from transformers import BertTokenizer, BertForSequenceClassification

model = BertForSequenceClassification.from_pretrained("DaNLP/da-bert-hatespeech-classification")
tokenizer = BertTokenizer.from_pretrained("DaNLP/da-bert-hatespeech-classification")
```

## Training data

The data used for training has not been made publicly available. It consists of social media data manually annotated in collaboration with Danmarks Radio.

