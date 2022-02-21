---
language: ms
---

# t5-base-bahasa-cased

Pretrained T5 base language model for Malay. 

## Pretraining Corpus

`t5-base-bahasa-cased` model was pretrained on multiple tasks. Below is list of tasks we trained on,

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