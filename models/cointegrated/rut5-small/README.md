---
language: "ru"
tags:
- paraphrasing
- russian
license: mit
---

This is a small Russian paraphraser based on the [google/mt5-small](https://huggingface.co/google/mt5-small) model. 
It has rather poor paraphrasing performance, but can be fine tuned for this or other tasks.

This model was created by taking the [alenusch/mt5small-ruparaphraser](https://huggingface.co/alenusch/mt5small-ruparaphraser) model and stripping 96% of its vocabulary which is unrelated to the Russian language or infrequent.

* The original model has 300M parameters, with 256M of them being input and output embeddings. 
* After shrinking the `sentencepiece` vocabulary from 250K to 20K the number of model parameters reduced to 65M parameters, and model size reduced from 1.1GB to 246MB.
   * The first 5K tokens in the new vocabulary are taken from the original `mt5-small`.
   * The next 15K tokens are the most frequent tokens obtained by tokenizing a Russian web corpus from the [Leipzig corpora collection](https://wortschatz.uni-leipzig.de/en/download/Russian).

The model can be used as follows:
```
# !pip install transformers sentencepiece
import torch
from transformers import T5ForConditionalGeneration, T5Tokenizer

tokenizer = T5Tokenizer.from_pretrained("cointegrated/rut5-small")
model = T5ForConditionalGeneration.from_pretrained("cointegrated/rut5-small")

text = 'Ехал Грека через реку, видит Грека в реке рак. '
inputs = tokenizer(text, return_tensors='pt')
with torch.no_grad():
    hypotheses = model.generate(
        **inputs, 
        do_sample=True, top_p=0.95, num_return_sequences=10, 
        repetition_penalty=2.5,
        max_length=32,
    )
for h in hypotheses:
    print(tokenizer.decode(h, skip_special_tokens=True))
```
