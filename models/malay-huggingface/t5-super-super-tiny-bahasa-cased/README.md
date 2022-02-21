---
language: ms
---

# t5-super-super-tiny-bahasa-cased

Pretrained T5 super-super-tiny language model for Malay. 

## Pretraining Corpus

`t5-super-super-tiny-bahasa-cased` model was pretrained on multiple tasks. Below is list of tasks we trained on,

1. Language masking task on bahasa news, bahasa Wikipedia, bahasa Academia.edu, bahasa parliament and translated The Pile.
2. News title prediction on bahasa news.
3. Next sentence prediction on bahasa news, bahasa Wikipedia, bahasa Academia.edu, bahasa parliament and translated The Pile.
4. Translated QA Natural.
5. Text Similarity task on translated SNLI and translated MNLI.
6. EN-MS translation.
7. MS-EN translation.
8. Abstractive Summarization.
9. Knowledge Graph triples generation.
10. Paraphrase.

Preparing steps can reproduce at https://github.com/huseinzol05/malaya/tree/master/pretrained-model/t5/prepare

## Pretraining details

- This model was trained using Google T5 repository https://github.com/google-research/text-to-text-transfer-transformer, on v3-8 TPU.
- All steps can reproduce from here, https://github.com/huseinzol05/Malaya/tree/master/pretrained-model/t5

## Load Pretrained Model

You can use this model by installing `torch` or `tensorflow` and Huggingface library `transformers`. And you can use it directly by initializing it like this:  

```python
from transformers import T5Tokenizer, T5Model

model = T5Model.from_pretrained('malay-huggingface/t5-super-super-tiny-bahasa-cased')
tokenizer = T5Tokenizer.from_pretrained('malay-huggingface/t5-super-super-tiny-bahasa-cased')
```

## Example using T5ForConditionalGeneration

```python
from transformers import T5Tokenizer, T5ForConditionalGeneration

tokenizer = T5Tokenizer.from_pretrained('malay-huggingface/t5-super-super-tiny-bahasa-cased')
model = T5ForConditionalGeneration.from_pretrained('malay-huggingface/t5-super-super-tiny-bahasa-cased')
input_ids = tokenizer.encode('soalan: siapakah perdana menteri malaysia?', return_tensors = 'pt')
outputs = model.generate(input_ids)
print(tokenizer.decode(outputs[0]))
```

Output is,

```
'Mahathir Mohamad'
```

## Supported prefix

1. `soalan: {string}`, trained using Natural QA.
2. `ringkasan: {string}`, for abstractive summarization.
3. `tajuk: {string}`, for abstractive title.
4. `parafrasa: {string}`, for abstractive paraphrase.
5. `terjemah Inggeris ke Melayu: {string}`, for EN-MS translation.
6. `terjemah Melayu ke Inggeris: {string}`, for MS-EN translation.
7. `grafik pengetahuan: {string}`, for MS text to EN Knowledge Graph triples format.
8. `ayat1: {string1} ayat2: {string2}`, semantic similarity.