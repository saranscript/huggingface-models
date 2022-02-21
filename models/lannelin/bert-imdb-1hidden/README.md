---
language: 
- en
datasets:
- imdb
metrics:
- accuracy
---

# bert-imdb-1hidden

## Model description

A `bert-base-uncased` model was restricted to 1 hidden layer and
fine-tuned for sequence classification on the 
imdb dataset loaded using the `datasets` library.

## Intended uses & limitations

#### How to use

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification

pretrained = "lannelin/bert-imdb-1hidden"

tokenizer = AutoTokenizer.from_pretrained(pretrained)

model = AutoModelForSequenceClassification.from_pretrained(pretrained)

LABELS = ["negative", "positive"]

def get_sentiment(text: str):
    inputs = tokenizer.encode_plus(text, return_tensors='pt')

    output = model(**inputs)[0].squeeze()

    return LABELS[(output.argmax())]

print(get_sentiment("What a terrible film!"))
```

#### Limitations and bias

No special consideration given to limitations and bias. 

Any bias held by the imdb dataset may be reflected in the model's output.

## Training data

Initialised with [bert-base-uncased](https://huggingface.co/bert-base-uncased)

Fine tuned on [imdb](https://huggingface.co/datasets/imdb)


## Training procedure

 The model was fine-tuned for 1 epoch with a batch size of 64, 
 a learning rate of 5e-5, and a maximum sequence length of 512.

## Eval results

Accuracy on imdb test set: 0.87132