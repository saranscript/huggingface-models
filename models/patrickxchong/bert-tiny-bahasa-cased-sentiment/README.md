---
language:
  - ms
  - en
license: apache-2.0
tags:
  - text-classification
  - sentiment-analysis
widget:
  - text: "Saya sangat gembira hari ini!"
---

# bert-tiny-bahasa-cased-sentiment

Proof of concept of creating a sentiment analysis model with using
https://huggingface.co/malay-huggingface/bert-base-bahasa-cased as the base model.

Tokenizer is copied directly from https://huggingface.co/malay-huggingface/bert-base-bahasa-cased.

Sentiment analysis fine tuning was done with data compiled by [huseinzol05](https://github.com/huseinzol05/) at https://github.com/huseinzol05/malay-dataset/tree/master/sentiment.
