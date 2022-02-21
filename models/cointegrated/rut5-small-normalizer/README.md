---
language: "ru"
tags:
- normalization
- denoising autoencoder
- russian
widget:
- text: "меня тобой не понимать"
license: mit
---
This is a small Russian denoising autoencoder. It can be used for restoring corrupted sentences.

This model was produced by fine-tuning the [rut5-small](https://huggingface.co/cointegrated/rut5-small) model on the task of reconstructing a sentence:
* restoring word positions (after slightly shuffling them)
* restoring dropped words and punctuation marks (after dropping some of them randomly)
* restoring inflection of words (after changing their inflection randomly using [natasha](https://github.com/natasha/natasha) and [pymorphy2](https://github.com/kmike/pymorphy2) packages)

The fine-tuning was performed on a [Leipzig web corpus](https://wortschatz.uni-leipzig.de/en/download/Russian) of Russian sentences. 

The model can be applied as follows:
```
# !pip install transformers sentencepiece
import torch
from transformers import T5ForConditionalGeneration, T5Tokenizer
tokenizer = T5Tokenizer.from_pretrained("cointegrated/rut5-small-normalizer")
model = T5ForConditionalGeneration.from_pretrained("cointegrated/rut5-small-normalizer")

text = 'меня тобой не понимать'
inputs = tokenizer(text, return_tensors='pt')
with torch.no_grad():
    hypotheses = model.generate(
        **inputs, 
        do_sample=True, top_p=0.95, 
        num_return_sequences=5, 
        repetition_penalty=2.5,
        max_length=32,
    )
for h in hypotheses:
    print(tokenizer.decode(h, skip_special_tokens=True))
```
A possible output is:
```
# Мне тебя не понимать.
# Если бы ты понимаешь меня?
# Я с тобой не понимаю.
# Я тебя не понимаю.
# Я не понимаю о чем ты.
```