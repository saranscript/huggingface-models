---
language: fa
tags:
- paraphrasing
datasets:
- tapaco
widget:
- text: "این یک مقالهٔ خرد آلمان است. می‌توانید با گسترش آن به ویکی‌پدیا کمک کنید."
- text: "برای خرید یک کتاب باید از فروشگاه اینترنتی استفاده کنید."

---

# Persian-t5-paraphraser

This is a paraphrasing model for the Persian language. It is based on [the monolingual T5 model for Persian.](https://huggingface.co/Ahmad/parsT5-base)

## Usage

```python

>>> pip install transformers
>>> from transformers import (T5ForConditionalGeneration, AutoTokenizer, pipeline)
>>> import torch

model_path = 'erfan226/persian-t5-paraphraser'
model = T5ForConditionalGeneration.from_pretrained(model_path)
tokenizer = AutoTokenizer.from_pretrained(model_path)
pipe = pipeline(task='text2text-generation', model=model, tokenizer=tokenizer)

def paraphrase(text):
  for j in range(5):
    out = pipe(text, encoder_no_repeat_ngram_size=5, do_sample=True, num_beams=5, max_length=128)[0]['generated_text']
    print("Paraphrase:", out)

text = "این یک مقالهٔ خرد آلمان است. می‌توانید با گسترش آن به ویکی‌پدیا کمک کنید."
print("Original:", text)
paraphrase(text)

# Original: این یک مقالهٔ خرد آلمان است. می‌توانید با گسترش آن به ویکی‌پدیا کمک کنید.
# Paraphrase: این یک مقالهٔ کوچک است.
# Paraphrase: این یک مقالهٔ کوچک است.
# Paraphrase: شما می توانید با گسترش این مقاله، به کسب و کار خود کمک کنید.
# Paraphrase: می توانید با گسترش این مقالهٔ خرد آلمان کمک کنید.
# Paraphrase: شما می توانید با گسترش این مقالهٔ خرد، به گسترش آن کمک کنید.

```

## Training data
This model was trained on the Persian subset of the [Tapaco dataset](https://huggingface.co/datasets/tapaco). It should be noted that this model was trained on a very small dataset and therefore the performance might not be as expected, for now.