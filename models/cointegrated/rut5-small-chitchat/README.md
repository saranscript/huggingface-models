---
language: "ru"
tags:
- dialogue
- russian
license: mit
---

This is a version of the [cointegrated/rut5-small](https://huggingface.co/cointegrated/rut5-small) model fine-tuned on some Russian dialogue data. It is not very smart and creative, but it is small and fast, and can serve as a fallback response generator for some chatbot or can be fine-tuned to imitate the style of someone.

The input of the model is the previous dialogue utterances separated by `'\n\n'`, and the output is the next utterance. 

The model can be used as follows:
```
# !pip install transformers sentencepiece
import torch
from transformers import T5ForConditionalGeneration, T5Tokenizer

tokenizer = T5Tokenizer.from_pretrained("cointegrated/rut5-small-chitchat")
model = T5ForConditionalGeneration.from_pretrained("cointegrated/rut5-small-chitchat")

text = 'Привет! Расскажи, как твои дела?'
inputs = tokenizer(text, return_tensors='pt')
with torch.no_grad():
    hypotheses = model.generate(
        **inputs, 
        do_sample=True, top_p=0.5, num_return_sequences=3, 
        repetition_penalty=2.5,
        max_length=32,
    )
for h in hypotheses:
    print(tokenizer.decode(h, skip_special_tokens=True))
# Как обычно.
# Сейчас - в порядке.
# Хорошо.
# Wall time: 363 ms 
```
