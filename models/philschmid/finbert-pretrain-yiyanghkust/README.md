---
pipeline_tag: "fill-mask"
language: en

---

# This repository is a fork of [yiyanghkust/finbert-pretrain](https://huggingface.co/yiyanghkust/finbert-pretrain)

> All credits to [@yiyanghkust](https://huggingface.co/yiyanghkust).

I added the TensorFlow model and a proper `tokenizer.json`

---

`FinBERT` is a BERT model pre-trained on financial communication text. The purpose is to enhance financial NLP research and practice. It is trained on the following three financial communication corpus. The total corpora size is 4.9B tokens.

- Corporate Reports 10-K & 10-Q: 2.5B tokens
- Earnings Call Transcripts: 1.3B tokens
- Analyst Reports: 1.1B tokens

More details on `FinBERT`'s pre-training process can be found at: https://arxiv.org/abs/2006.08097

`FinBERT` can be further fine-tuned on downstream tasks. Specifically, we have fine-tuned `FinBERT` on an analyst sentiment classification task, and the fine-tuned model is shared at https://huggingface.co/yiyanghkust/finbert-tone