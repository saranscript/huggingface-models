---
language: fr
tags:
- pytorch
- t5
- seq2seq
- summarization
datasets: cnn_dailymail
---

# French T5 Abstractive Text Summarization

Version 1.0 (I will keep improving the model's performances.)

## Model description

This model is a T5 Transformers model (JDBN/t5-base-fr-qg-fquad) that was fine-tuned in french for abstractive text summarization.

## How to use

```python
from transformers import T5Tokenizer, T5ForConditionalGeneration
tokenizer = T5Tokenizer.from_pretrained("plguillou/t5-base-fr-sum-cnndm")
model = T5ForConditionalGeneration.from_pretrained("plguillou/t5-base-fr-sum-cnndm")
```

To summarize an ARTICLE, just modify the string like this : "summarize: ARTICLE".

## Training data

The base model I used is JDBN/t5-base-fr-qg-fquad (it can perform question generation, question answering and answer extraction).

I used the "t5-base" model from the transformers library to translate in french the CNN / Daily Mail summarization dataset.

