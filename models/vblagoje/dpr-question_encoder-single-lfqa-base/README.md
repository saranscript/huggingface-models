---
language: en
datasets:
- vblagoje/lfqa
license: mit
---

## Introduction
The question encoder model based on [DPRQuestionEncoder](https://huggingface.co/docs/transformers/master/en/model_doc/dpr#transformers.DPRQuestionEncoder) architecture. It uses the transformer's pooler outputs as question representations. 

## Training
We trained vblagoje/dpr-question_encoder-single-lfqa-base using FAIR's dpr-scale starting with PAQ based pretrained checkpoint and fine-tuned the retriever on the question-answer pairs from the LFQA dataset. As dpr-scale requires DPR formatted training set input with positive, negative, and hard negative samples - we created a training file with an answer being positive, negatives being question unrelated answers, while hard negative samples were chosen from answers on questions between 0.55 and 0.65 of cosine similarity. 

## Performance
LFQA DPR-based retriever (vblagoje/dpr-question_encoder-single-lfqa-base and vblagoje/dpr-ctx_encoder-single-lfqa-base) had a score of 6.69 for R-precision and 14.5 for Recall@5 on KILT benchmark. 

## Usage


```python
from transformers import DPRContextEncoder, DPRContextEncoderTokenizer

model = DPRQuestionEncoder.from_pretrained("vblagoje/dpr-question_encoder-single-lfqa-base").to(device)
tokenizer = AutoTokenizer.from_pretrained("vblagoje/dpr-question_encoder-single-lfqa-base")

input_ids = tokenizer("Why do airplanes leave contrails in the sky?", return_tensors="pt")["input_ids"]
embeddings = model(input_ids).pooler_output
```

## Author
- Vladimir Blagojevic: `dovlex [at] gmail.com` [Twitter](https://twitter.com/vladblagoje) | [LinkedIn](https://www.linkedin.com/in/blagojevicvladimir/)