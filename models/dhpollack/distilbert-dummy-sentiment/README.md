---
language:
- "multilingual"
- "en"
tags:
- "sentiment-analysis"
- "testing"
- "unit tests"
---
# DistilBert Dummy Sentiment Model

## Purpose

This is a dummy model that can be used for testing the transformers `pipeline` with the task `sentiment-analysis`.  It should always give random results (i.e. `{"label": "negative", "score": 0.5}`).

## How to use

```python
classifier = pipeline("sentiment-analysis", "dhpollack/distilbert-dummy-sentiment")
results  = classifier(["this is a test", "another test"])
```

## Notes

This was created as follows:

1. Create a vocab.txt file (in /tmp/vocab.txt in this example).

```
[UNK]
[SEP]
[PAD]
[CLS]
[MASK]
```

2. Open a python shell:

```python
import transformers
config = transformers.DistilBertConfig(vocab_size=5, n_layers=1, n_heads=1, dim=1, hidden_dim=4 * 1, num_labels=2, id2label={0: "negative", 1: "positive"}, label2id={"negative": 0, "positive": 1})
model = transformers.DistilBertForSequenceClassification(config)
tokenizer = transformers.DistilBertTokenizer("/tmp/vocab.txt", model_max_length=512)
config.save_pretrained(".")
model.save_pretrained(".")
tokenizer.save_pretrained(".")
```
