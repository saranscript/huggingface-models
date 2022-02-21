---
language: fa
tags:
- text-generation
widget:
 - text: "در یک اتفاق شگفت انگیز، پژوهشگران"
 - text: "گرفتگی بینی در کودکان و به‌خصوص نوزادان باعث می‌شود"
 - text: "امیدواریم نوروز امسال سالی"
---

# GPT2 Medium 4 Persian
> This is part of the
[Flax/Jax Community Week](https://discuss.huggingface.co/t/pretrain-gpt2-from-scratch-in-persian/7560), organized by [HuggingFace](https://huggingface.co/) and TPU usage sponsored by Google.


## Team Members
- [Mehrdad Farahani](huggingface.co/m3hrdadfi)
- [Saied Alimoradi](https://discuss.huggingface.co/u/saied)
- [M. Reza Zerehpoosh](huggingface.co/ironcladgeek)
- [Hooman Sedghamiz](https://discuss.huggingface.co/u/hooman650)
- [Mazeyar Moeini Feizabadi](https://discuss.huggingface.co/u/mazy1998)

## Dataset
We used  [Oscar](https://huggingface.co/datasets/oscar) dataset, which is a huge multilingual corpus obtained by language classification and filtering of the Common Crawl corpus.

## How To Use
You can use this model directly with a pipeline for text generation.

```python
from transformers import pipeline, AutoTokenizer, GPT2LMHeadModel
tokenizer = AutoTokenizer.from_pretrained('flax-community/gpt2-medium-persian')
model = GPT2LMHeadModel.from_pretrained('flax-community/gpt2-medium-persian')
generator = pipeline('text-generation', model, tokenizer=tokenizer, config={'max_length':100})
generated_text = generator('در یک اتفاق شگفت انگیز، پژوهشگران')
```
For using Tensorflow import TFGPT2LMHeadModel instead of GPT2LMHeadModel.
## Demo

... SOON

## Evaluation

... SOON