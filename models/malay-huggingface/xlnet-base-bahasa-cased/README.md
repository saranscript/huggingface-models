---
language: ms
---

# xlnet-base-bahasa-cased

Pretrained XLNET base language model for Malay.

## Pretraining Corpus

`xlnet-base-bahasa-cased` model was pretrained on ~1.4 Billion words. Below is list of data we trained on,

1. [cleaned local texts](https://github.com/huseinzol05/malay-dataset/tree/master/dumping/clean).
2. [translated The Pile](https://github.com/huseinzol05/malay-dataset/tree/master/corpus/pile).

## Pretraining details

- All steps can reproduce from here, [Malaya/pretrained-model/xlnet](https://github.com/huseinzol05/Malaya/tree/master/pretrained-model/xlnet).

## Load Pretrained Model

You can use this model by installing `torch` or `tensorflow` and Huggingface library `transformers`. And you can use it directly by initializing it like this:  

```python
from transformers import XLNetModel, XLNetTokenizer

model = XLNetModel.from_pretrained('malay-huggingface/xlnet-base-bahasa-cased')
tokenizer = XLNetTokenizer.from_pretrained(
    'malay-huggingface/xlnet-base-bahasa-cased',
    do_lower_case = False,
)
```