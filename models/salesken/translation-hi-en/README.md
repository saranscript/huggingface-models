---
license: apache-2.0
language: 
- hi
tags:
- translation
- salesken
- hi
- opus-mt
---
opus-mt model finetuned on ai4bhart Hindi-English parallel corpora (SAMANANTAR)

source-language: Hindi

target-language: English


```python


from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
tokenizer = AutoTokenizer.from_pretrained("salesken/translation-hi-en")
model = AutoModelForSeq2SeqLM.from_pretrained("salesken/translation-hi-en")

hin_snippet = "कोविड के कारण हमने अपने ऋण ब्याज को कम कर दिया है"
inputs = tokenizer.encode(
    hin_snippet, return_tensors="pt",padding=True,max_length=512,truncation=True)

outputs = model.generate(
    inputs, max_length=128, num_beams=None, early_stopping=True)

translated = tokenizer.decode(outputs[0]).replace('<pad>',"").strip().lower()
print(translated)
# due to covid, we have reduced our debt interest


```