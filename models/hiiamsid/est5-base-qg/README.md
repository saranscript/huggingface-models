---
language: ["es"]
tags:
- spanish
- question generation
- qg
Datasets:
- SQUAD
license: mit
---
This is the finetuned model of hiiamsid/est5-base for Question Generation task.
* Here input is the context only and output is questions. No information regarding answers were given to model. 
* Unfortunately, due to lack of sufficient resources it is fine tuned with batch_size=10 and num_seq_len=256. So, if too large context is given model may not get information about last portions.

```
from transformers import T5ForConditionalGeneration, T5Tokenizer
MODEL_NAME = 'hiiamsid/est5-base-qg'
model = T5ForConditionalGeneration.from_pretrained(MODEL_NAME)
tokenizer = T5Tokenizer.from_pretrained(MODEL_NAME)
model.cuda();
model.eval();
def generate_question(text, beams=10, grams=2, num_return_seq=10,max_size=256):
    x = tokenizer(text, return_tensors='pt', padding=True).to(model.device)
    out = model.generate(**x, no_repeat_ngram_size=grams, num_beams=beams, num_return_sequences=num_return_seq, max_length=max_size)
    return tokenizer.decode(out[0], skip_special_tokens=True)
print(generate_question('Any context in spanish from which question is to be generated'))

```

## Citing & Authors
- Datasets : [squad_es](https://huggingface.co/datasets/squad_es)
- Model : [hiiamsid/est5-base](hiiamsid/est5-base)